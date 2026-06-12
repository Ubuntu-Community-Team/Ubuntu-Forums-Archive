---
title: "cannot use vagrant on Xenial"
date: 2016-04-03
forum: Ubuntu Development Version
---

### Post by enboig on 2016-04-03
I don't know if this is a xenial bug. I just installed *vagrant* but I cannot use it, I get this error:
```

$ vagrant box add hashicorp/precise64
/usr/lib/ruby/vendor_ruby/i18n/backend/base.rb:184:in `rescue in load_yml': can not load translations from /usr/lib/ruby/locales/en.yml: #<Errno::ENOENT: No such file or directory @ rb_sysopen - /usr/lib/ruby/locales/en.yml> (I18n::InvalidLocaleData)
	from /usr/lib/ruby/vendor_ruby/i18n/backend/base.rb:181:in `load_yml'
	from /usr/lib/ruby/vendor_ruby/i18n/backend/base.rb:165:in `load_file'
	from /usr/lib/ruby/vendor_ruby/i18n/backend/base.rb:15:in `block in load_translations'
	from /usr/lib/ruby/vendor_ruby/i18n/backend/base.rb:15:in `each'
	from /usr/lib/ruby/vendor_ruby/i18n/backend/base.rb:15:in `load_translations'
	from /usr/lib/ruby/vendor_ruby/i18n/backend/simple.rb:57:in `init_translations'
	from /usr/lib/ruby/vendor_ruby/i18n/backend/simple.rb:40:in `available_locales'
	from /usr/lib/ruby/vendor_ruby/i18n/config.rb:43:in `available_locales'
	from /usr/lib/ruby/vendor_ruby/i18n/config.rb:49:in `available_locales_set'
	from /usr/lib/ruby/vendor_ruby/i18n.rb:278:in `locale_available?'
	from /usr/lib/ruby/vendor_ruby/i18n.rb:284:in `enforce_available_locales!'
	from /usr/lib/ruby/vendor_ruby/i18n.rb:151:in `translate'
	from /usr/lib/ruby/vendor_ruby/vagrant/action/builtin/box_add.rb:167:in `add_from_metadata'
	from /usr/lib/ruby/vendor_ruby/vagrant/action/builtin/box_add.rb:104:in `call'
	from /usr/lib/ruby/vendor_ruby/vagrant/action/warden.rb:34:in `call'
	from /usr/lib/ruby/vendor_ruby/vagrant/action/builder.rb:116:in `call'
	from /usr/lib/ruby/vendor_ruby/vagrant/action/runner.rb:66:in `block in run'
	from /usr/lib/ruby/vendor_ruby/vagrant/util/busy.rb:19:in `busy'
	from /usr/lib/ruby/vendor_ruby/vagrant/action/runner.rb:66:in `run'
	from /usr/share/vagrant/plugins/commands/box/command/add.rb:78:in `execute'
	from /usr/share/vagrant/plugins/commands/box/command/root.rb:61:in `execute'
	from /usr/lib/ruby/vendor_ruby/vagrant/cli.rb:42:in `execute'
	from /usr/lib/ruby/vendor_ruby/vagrant/environment.rb:268:in `cli'
	from /usr/bin/vagrant:173:in `<main>'

```

What can I do? I want to use it for developing PHP.

thanks

---

### Post by howefield on 2016-04-04
Thread moved to the "*Ubuntu Development Version*" forum.

---

### Post by Frankie_Robertson on 2016-04-11
The package provided upstream (labelled Debian) available at [https://www.vagrantup.com/downloads.html](https://www.vagrantup.com/downloads.html) works fine.

---

