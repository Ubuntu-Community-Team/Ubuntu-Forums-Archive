---
title: "Domain controller ubuntu 9.10 for windows 7"
date: 2011-02-11
forum: Server Platforms
---

### Post by maikel.b on 2011-02-11
Hello, 

I need a little bit help with a samba domain controller, i am working more than 6 hours to fix the problem bud its still NOT working,,,

First the things i did, i installed the server 9.10 ubuntu, then i installed samba, changed the needed settings for the samba server, and try to login tot the server with a fresh install of windows 7

The windows 7 box is complaining about dns? can't find the domain test that i installed on the ubuntu 9.10 server and is complaining about test is not a root dns bla bla bla.. I called the domain TEST...

The bad thing is, i don't have my smb.conf anymore, because i where mad, and deleted the server in VMware..

So my question is, is there someone on this form that can help me??? 

I want to create a domain controller for windows 7, if the windows 7 box crashes i replaced for a new windows 7 and log back in on my domain controller, en everything stores on the domain controller is not lost.. such as pictures?? or data for my job.. etc

So i need HELP.. please, the domain controller is driving me crazy!!:confused::confused::confused::confused::confused::confused::confused::confused:

Thanks for all your solutions..

Kinds regards Maikel.   

Is it possible to post all the comments that i need for the smb.conf file???

And my question is also, is a dns server required for the windows 7 box to accept the controller???

Manny thanks !!!!!

---

### Post by rudelgurke on 2011-02-11
There's a long description in the Samba Wiki what you'll all need:

[http://wiki.samba.org/index.php/Samba4/HOWTO#Windows7](http://wiki.samba.org/index.php/Samba4/HOWTO#Windows7)

And even on the MS forums a thread about how to configure the Windows side security settings:

[http://social.msdn.microsoft.com/forums/en-US/windowsgeneraldevelopmentissues/thread/80b401a1-1da2-43a3-a803-4136492483b0/](http://social.msdn.microsoft.com/forums/en-US/windowsgeneraldevelopmentissues/thread/80b401a1-1da2-43a3-a803-4136492483b0/)


Still - if you want to backup your data, don't you think a backup program might be the better choice ?

---

### Post by maikel.b on 2011-02-11
Hey hello, thanks for your replay, 

Its not a backup solution for me, bud this thing I must install for a client of me.
 
I will also backup the domain controller, bud thanks for your information..

I will read the instruction on the site's and try it on my VM machine.

I got it running under windows xp, now is my goal to fix it with windows 7.

Do you have the same configuration running? Domain domain controller with windows 7?

greets maikel.

---

### Post by rudelgurke on 2011-02-12
I've it running - yes. Still the fix on the MS page had to be applied.
However I've the entire setup running (DNS + Kerberos + LDAP + Samba).

---

