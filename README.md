# ChatSpace DB設計

## groups_usersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user

## groupテーブル

|Column|Type|Options|
|------|----|-------|
|id|integer|null: false|
|grpname|string|null: false|
|user_id|integer|null: false foreign_key: true|

### Association
- has_many :groups_users
- has_many :users through: :groups_users
- has_many :messages

## userテーブル

|Column|Type|Options|
|------|----|-------|
|id|integer|null: false|
|nickname|string|null: false|
|mail|string|null: false|
|pass|string|null: false|

### Association
- has_many :groups_users
- has_many :groups through: :groups_users
- has_many :messages


## messagesテーブル

|Column|Type|Options|
|------|----|-------|
|body|text||
|image|string||
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user