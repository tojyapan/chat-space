# DB設計

## users

|Column|Type|Options|
|------|----|-------|
|username|string|null: false|
|email|string|null: false, unique: true|
|password|string|null: false|
|group_user_id|integer|null: false, foreign_key: true|

### Association
- has_many :messages
- has_many :groups, through: :group_users

## messages

|Column|Type|Options|
|------|----|-------|
|body|text|null: false|
|image|string||
|group_id|integer|null: false, foreign_key: true|
|user_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :user
- belongs_to :group

## groups

|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|group_user_id|integer|null: false, foreign_key: true|

### Association
- has_many :users, through: :group_users

## group_users

|Column|Type|Options|
|------|----|-------|
|group_id|integer|null: false, foreign_key: true|
|user_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user