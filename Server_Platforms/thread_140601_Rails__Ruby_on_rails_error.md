---
title: "Rails / Ruby on rails error"
date: 2006-03-06
forum: Server Platforms
---

### Post by Hendrik_ on 2006-03-06
Hello there,

I've the following error when i run a rails command, while the installation of rails/ruby went without any errors

*~/ruby$ rails /home/hendrik/ruby/test
/usr/lib/ruby/gems/1.8/gems/activesupport-1.2.5/lib/active_support/dependencies.rb:200:in `const_missing': uninitialized constant Base (NameError)
from /usr/lib/ruby/gems/1.8/gems/actionpack-1.11.2/lib/action_view.rb:30
from /usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:21:in `require__'
from /usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:21:in `require'
from /usr/lib/ruby/gems/1.8/gems/activesupport-1.2.5/lib/active_support/dependencies.rb:214:in `require'
from /usr/lib/ruby/gems/1.8/gems/actionpack-1.11.2/lib/action_controller.rb:58
from /usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:21:in `require__'
from /usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:21:in `require'
from /usr/lib/ruby/gems/1.8/gems/activesupport-1.2.5/lib/active_support/dependencies.rb:214:in `require'
from /usr/local/lib/site_ruby/1.8/rubygems.rb:182:in `activate'
from /usr/local/lib/site_ruby/1.8/rubygems.rb:181:in `each'
from /usr/local/lib/site_ruby/1.8/rubygems.rb:181:in `activate'
from /usr/local/lib/site_ruby/1.8/rubygems.rb:167:in `activate'
from /usr/local/lib/site_ruby/1.8/rubygems.rb:166:in `each'
from /usr/local/lib/site_ruby/1.8/rubygems.rb:166:in `activate'
from /usr/local/lib/site_ruby/1.8/rubygems.rb:37:in `require_gem_with_options'
from /usr/local/lib/site_ruby/1.8/rubygems.rb:31:in `require_gem'
from /usr/bin/rails:17


I'm quite new to linux, so i'm sure i've forgotten something :)

Thanks for your support,
Hendrik.

---

### Post by Blacktalon on 2006-10-31
Wow this forum is old, anyways I am starting to get use to doing some trouble shooting for minor problems in rails.

Question 1: have you done? (in terminal) sudo apt-get install ruby irb rdoc
Question 2: do you have RubyGems? if not you can get it here:  [http://rubyforge.org/frs/download.php/11289/rubygems-0.9.0.tgz](http://rubyforge.org/frs/download.php/11289/rubygems-0.9.0.tgz)


Sorry it took so long for a replie

Everyone deserves a reply!

---

