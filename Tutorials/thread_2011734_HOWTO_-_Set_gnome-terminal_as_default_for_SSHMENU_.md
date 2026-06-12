---
title: "HOWTO - Set gnome-terminal as default for SSHMENU on 12.04"
date: 2012-06-27
forum: Tutorials
---

### Post by bouwerik on 2012-06-27
Hi all,

Here is a short modification of the sshmenu program. I modifies a config file so that not the default xterm is loaded on creating a connection, but the more eye-candy gnome-terminal. 
I especially needed this because sshmenu-gnome is no longer available on 12.04 (missing dependency libgnome2-ruby)

Ok, edit the file sshmenu.rb:
```
sudo vi /usr/lib/ruby/1.8/sshmenu.rb
```

then scroll to line 1096 or in vi search using /xterm

replace:
```
command = "#{host.env_settings}xterm -T " + shell_quote(host.title)
```

with:
```
command = "gnome-terminal"
```

then on line 1101, replace:
```
command += ' -e sh -c ' +
```

with:
```
command += ' -e ' +
```

Save this bad boy, restart sshmenu and you are all set.

Cheerio to the lads!

Erik
Studio Orange Netherlands

---

