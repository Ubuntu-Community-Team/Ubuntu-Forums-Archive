---
title: "Needing Squid3 config help."
date: 2015-07-23
forum: Server Platforms
---

### Post by Higgins909 on 2015-07-23
Just got my VM server up and installed package "squid3"
I've changed a few things, like adding in my old refresh patterns and uncommented acl localnet src 192.168.0.0/16 # RFC1918 possible internal network.

    The problems I'm having right now is that its still refusing connections and I do see a http_access deny all
but don't know what to change it to.  If I change it to allow, what is it really allowing? I seen some allow authenticated, but didn't want that.
I wanted to have it setup so anyone/only on my private local home network can use it, without usernames n passwords.  Like before. (I know part of it was the acl up there and it not being port forwarded)
I'm also not quite sure how to setup a cache. all I remember from my old ones was location size ufs 256 256.
    I'm worried I will have to even rebuild my caches. I don't know how to do that.

I used to use webmin, but am trying to break that.  That's why I don't know anything.

Thanks,
    Higgins909

---

