# README

## usersテーブル
|Column  |Type   |Options|
|--------|-------|-------|
|id      |integer|null: false, foreign_key: true|
|name    |string |null: false|
|email   |string |null: false|
|password|string |null: false|
### Association
- has_many :ress, dependent: :destroy
- has_many :threads, through: :users_threads
- has_many :users_threads


## threadsテーブル
|Column    |Type   |Options|
|----------|-------|-------|
|id        |integer|null: false, foreign_key: true|
|name      |string |null: false|
|created_by|integer|  |
|updated_by|integer|  |
### Association
- has_many :ress
- has_many :users, through: :uses_threads
- has_many :users_threads
- has_many :categorys, through: :threads_categorys
- has_many :threads_categorys


## categorysテーブル
|Column  |Type   |Options|
|--------|-------|-------|
|id      |integer|null: false, foreign_key: true|
|text    |text   |       |
### Association
- has_many :ress
- has_many :users, through: :uses_threads
- has_many :users_threads


## users_threadsテーブル
|Column  |Type   |Options|
|--------|-------|-------|
|user_id |integer|null: false, foreign_key: true|
|thread_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :thread


## threads_categorysテーブル
|Column  |Type   |Options|
|--------|-------|-------|
|thread_id  |integer|null: false, foreign_key: true|
|category_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :thread
- belongs_to :category


## ressテーブル
|Column  |Type   |Options|
|--------|-------|-------|
|id       |integer|null: false, foreign_key: true|
|text     |text   |                              |
|user_id  |integer|null: false, foreign_key: true|
|thread_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :thread