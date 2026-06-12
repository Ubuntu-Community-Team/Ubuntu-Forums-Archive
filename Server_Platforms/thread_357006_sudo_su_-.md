---
title: "sudo su -"
date: 2007-02-09
forum: Server Platforms
---

### Post by firebadger on 2007-02-09
Is there any essential difference between logging in as root using a root password and becoming root by running... ```
sudo su -
``` ...and providing your own password?

---

### Post by MrHorus on 2007-02-09
Not really.

You will inherit root's path using ```
su -
``` just like if you had logged in normally.

---

### Post by alasdair.mccall on 2007-02-09
Nope!

Virutally all experienced Linux users will say that you should hardly ever log in and work as root. This is not so much a security concern as just a good practise that will keep you from doing un-intentional harm to your PC. However, with that said, most of these Linux users (myself included) ignore this advice simply because they feel that they know what they are doing! :) 

sudo provides a neat way of executing root commands in a safe and controlled way. If a user is sudo enabled - 'Administer the System' option under User properties in User and Group settings - that user is then able to issue root commands using sudo and using their password as authentication. This eliminates the need to su (change user) to root, issue the command and then, according to good but often ignored Linux practises, leave the root user.

An additional benefit is that you never need to remember root's password, just your own. You can also su to root, even if you've forgotten root's password, which can be very uselful and handy when you've been away from your PC for a long time.

---

### Post by firebadger on 2007-02-09
That confirms what I thought.  It was just that I often hear people lamenting the fact that they can't get a root prompt on Ubuntu when it seemed to me really easy using this approach.  I thought perhaps there was something more to it.
I tend only to use this method to get a root prompt when I am doing quite a lot of administrative tasks.  I'm quite confident in myself that I'm not going to do anything daft.

Thanks!

---

### Post by Titus A Duxass on 2007-02-09
When you are doing a lot of admin tasks you can do "sudo -i" which will put you at a root prompt, thus negating the need to sudo everything.  Type "exit" to get back to the normal user prpmpt.

---

