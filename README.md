### CarrierWave
---

https://github.com/carrierwaveuploader/carrierwave

```
gem install carrierwave
Gemfile
gem 'carrierwave', '~> 1.0'
rails g uploader Avatar
app/uploaders/avatar_uploader.rb
class AvatarUploader < CarrierWave::Uploader::Base
  storage :file
end

uploader = AvatarUploader.new
uploader.store!(my_file)
uploader.retrieve_from_store!('my_file.png')

- ActiveRecord
require 'carrierwave/orm/activerecord'
rails g migration add_avatar_to_users avatar:string
rake db:migrate
class User < ActiveRecord::Base
  mount_uploader :avatar, AvatarUploader
end

u = User.new
u.avatar = params[:file]

File.oepn('somewhere') do |f|
  u.avatar = f
end

u.save!
u.avatar.url
u.avatar.current_path
u.avatar_identifier

rails g migration add_avatar_to_users avatars:json
rake db:migrate
rails g migration add_avatars_to _users avatars:string
rake db:migrate

class User < ActiveRecord::Base
  mount_uploaders :avatars, AvatarUploader
  serialize :avatars, JSON
end

...


```


