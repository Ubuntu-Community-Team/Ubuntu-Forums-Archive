---
title: "Mount point to all group users"
date: 2013-03-21
forum: Server Platforms
---

### Post by Rait.H on 2013-03-21
Hello, I am not sure if the thread title is good enough to explain my problem, but I will explain. 
I am trying to make a **mount --bind /dir/www /home/user/www** for each user that is in **www** group. So all users that are in the **www** group will get that mount --bind to their home directory. Is this even possible and how can I do this if its possible. 

If you know how to do it in **Ruby** that would be even better because I am using **Chef**

Thank you.

---

### Post by schragge on 2013-03-21
Cannot say for ruby (you probably need the [etc]("http://ruby-doc.org/stdlib-1.9.2/libdoc/etc/rdoc/Etc.html") module to do this), but in a shell script this would be something like
```

for u in `getent group www|cut -d: -f4|tr , ' '`
do sudo mount --bind /dir/www /home/$u/www
done

```

[highlight]Update.[/highlight]
You get the member list of a group in ruby with
```
ruby -e 'require "etc";puts Etc.getgrname("www").mem'
```
Applying this to your data, I get something like
```

#!/usr/bin/ruby
require 'etc'

Etc.getgrnam('www').mem.each {|u|
        system("[COLOR=red]echo[/COLOR] mount --bind /dir/www /home/#{u}/www")
}

``` Replace [COLOR=red]echo[/COLOR] with sudo for this to do the real job.

---

### Post by Rait.H on 2013-03-21
Thanks :) 

This helped me a lot :)

---

