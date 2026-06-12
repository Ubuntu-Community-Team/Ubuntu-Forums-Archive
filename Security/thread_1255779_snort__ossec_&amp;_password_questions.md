---
title: "snort / ossec &amp; password questions"
date: 2009-09-01
forum: Security
---

### Post by Lori700698 on 2009-09-01
I'm so sorry to be a pain, I'm trying hard not to repeat my prior mistakes of being oblivious to my security needs and getting hacked again.

1.  Does snort & ossec have the ability to email reports or are they only viewed on the web interface?  These look to be excellent tools that would eliminate the need for multiple programs (like combos of tripwire, chkroot, and fail2ban.)  These look like they cover much of what most of these other programs do...or am I mistaken?

2. Can I use special characters in user names and passwords?
Like % * or $

3.  Is there any files I can trust to backup and re-use on my new install?

4.Looking over my hacked system log files, can somebody tell me if this is unusual? It was in the Kernel portion of the Logwatch and there is a ton of them.
 
1 Time(s): type=1503 audit(1251693195.403:59): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=104 name="/proc/4378/net/if_inet6" pid=4379 profile="/usr/sbin/named"

Thanks a lot!!!
Lori

---

### Post by TuckLive on 2009-09-02
> **Lori700698 said:**
> 
1.  Does snort & ossec have the ability to email reports or are they only viewed on the web interface?  These look to be excellent tools that would eliminate the need for multiple programs (like combos of tripwire, chkroot, and fail2ban.)  These look like they cover much of what most of these other programs do...or am I mistaken?

2. Can I use special characters in user names and passwords?
Like % * or $

3.  Is there any files I can trust to backup and re-use on my new install?

Lori

1.  OSSEC can email reports and this function is built in and easy to enable.

2.  I don't have a password for my web gui for OSSEC, but I do have a password for BASE and I have special characters.  If your installing Snort I recommend using BASE.

3.  If you have a backup copy of your files before it was hacked then I would use that.  Otherwise, I wouldn't reuse any files unless they are personal and you require them.

I just recently rebuilt my IDS and posted all the programs I'm using on my blog.  That post is [removed].

---

### Post by noway2 on 2009-09-02
Follow the instructions in Bodi Zazen's sticky post on installing snort and ossec.  It is very well written and the install should go smoothly.

Otherwise, what TuckLive said is correct.

On item 4, /usr/sbin/named sounds like a dns server daemon, named = name-daemon, as Bind referes to itself.  The log entry could mean that there is a configuration problem with Bind, assuming you are using it.

---

### Post by Lori700698 on 2009-09-02
> **Lori700698 said:**
> 
4.Looking over my hacked system log files, can somebody tell me if this is unusual? It was in the Kernel portion of the Logwatch and there is a ton of them.
 
1 Time(s): type=1503 audit(1251693195.403:59): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=104 name="/proc/4378/net/if_inet6" pid=4379 profile="/usr/sbin/named"



I figured this out this morning, and it was just a regular error not due to hack!
/etc/apparmor.d/usr.sbin.named.
ADD
/etc/bind/zones/** rw,

(After looking at the bind file closer this is not a good idea, the file actually states that bind should be read-only)

Here is the correct fix if anybody has this issue:
edit /etc/apparmor.d/usr.sbin.named and change the line

/proc/net/if_inet6 r,

to

/proc/**/net/if_inet6 r,

then restart apparmor and bind9

Thanks for the other advice, I appreciate it a lot!
Lori

---

### Post by bodhi.zazen on 2009-09-02
I was going to post, that is apparmor ...

See : [http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

but it looks as as if you know that already, w00t !!!

---

### Post by Lori700698 on 2009-09-02
I was working on getting snort running and I'm having a tad of an issue with the base.  It works in IE and Foxfire on my laptop, but it don't work right with my Foxfire portable it looks all jumbled up, is there an extension for this?  I use the portable a lot because I'm hardly ever home and it has all my bookmarks (I even plug it in when I get home half the time) x-httpd-php seems to be what portable is looking for.

Thanks,...I'm slowly getting things back together!
Lori

If anybody has this issue the solution is VERY simple.. 
[http://yourip/base/index.php](http://yourip/base/index.php)
You have to type the /index.php for Foxfire portable to stop trying to download it as a file instead of opening it up as a web page.

---

