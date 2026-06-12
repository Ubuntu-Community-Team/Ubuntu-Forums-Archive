---
title: "PHP5 and mybb"
date: 2010-05-31
forum: Server Platforms
---

### Post by NullHead on 2010-05-31
I help run a small time forum website for a group of my friends, and we decided to upgrade our server, hosted by linode, from Ubuntu 9.10, to Ubuntu 10.04. 

Afterwords, we started noticing that there seems to be a malfunction with PHP. 



I'm not sure where to start looking for this kind of thing, but all appears to be as it was before the upgrade.

Does anybody have any idea as to what the issue might be? 

PS: A normal forum post should look like this: 



PPS: My PHP version is 5.3.2-1ubuntu4.2

---

### Post by new_tolinux on 2010-05-31
I guess you had the magic_quotes_* settings [off] in your previous php.ini.
Yet they're probably on and yet escaping backslashes which where placed to escape ' or ".

Edit:
Setting them to "off" again probably will _not_ correct your current messages. You will have to produce new messages to test that. And you'll need to restart the apache-service as soon as you saved your new php.ini

---

### Post by NullHead on 2010-05-31
We ended up reverting to our old installation. We had shrunk our partition and duplicated it via the linode CP. We'll just stick with 9.10 for now. 

I played with it for a few hours and ended up giving up. All is well again. 

Thanks for your response anyways though!

---

