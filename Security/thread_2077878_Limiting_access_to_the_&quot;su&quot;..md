---
title: "Limiting access to the &quot;su&quot;."
date: 2012-10-29
forum: Security
---

### Post by kleenex on 2012-10-29
Hello, I would like to know one thing: in *buntu 12.04 (I do not know if others too) there is a group called **adm**. I would like to limit access to the "su" program by doing something like this:
```
[COLOR=Blue]sudo[/COLOR] chown root:admin /bin/su  
[COLOR=Blue]sudo[/COLOR] chmod 04750 /bin/su
``` As You can see, there is group called **admin**, but as I already mentioned in Ubuntu is different one - **adm**. So, should I do it this way?;
```
[COLOR=Blue]sudo[/COLOR] chown root:adm /bin/su  
[COLOR=Blue]sudo[/COLOR] chmod 04750 /bin/su
``` To limit access to **su** I should **admin **to **adm**, right? This question seems so simple... Thanks.

---

### Post by zombifier25 on 2012-10-29
Users in the "adm" group is allowed to view log files. The proper group for users allowed to do administrative task is "sudo" (formerly "admin", but it was changed in 12.04 in order to be compatible with upstream Debian)

(You should be clearer in your question. You want to limit access to "su" to who?)

---

### Post by Wim Sturkenboom on 2012-10-30
As long as your users don't give their passwords away, I can not see a need to block su. And if your users do give them away, nothing stops people that know the password from gaining access to that user account ;)

---

### Post by danelwillis on 2012-10-30
Unless People need specific Admin Access you should always give them a limited account so they cant break it.

---

### Post by sisco311 on 2012-10-30
May I ask you why?

On a local computer, where users are allowed to start a new login section, limiting the access to su doesn't makes much sense. 


On some Unix/Linux systems only users from the *wheel* group are allowed to su to root. For philosophical reasons GNU/su doesn't support the wheel group. See:
```
info coreutils 'su invocation'
```
(scroll down to the section by Richard Stallman)

If you have a valid reason for limiting the access to su , then you should write a pam rule.

Check out:
```
man pam_wheel
```
and the content of the **/etc/pam.d/su** file.

---

### Post by CharlesA on 2012-10-30
+1 to everyone else. I don't really see any problem with su by itself. If you don't want something to have admin rights, don't add them to the sudo group.

Outside of using sudo to become root, there is little that can be done with su unless you know the other user's password.

---

### Post by kleenex on 2012-10-30
Hi guys. I decided, that I will answer to everyone at once, okay? Computer on which I wanted to limit access to '**su**' is used to test various solutions. And one of these tests is limiting already mentioned access to '**su**'. Nothing more, nothing less. I also plan to test a lot of other things, but this is not the appropriate topic to write about it. According to all opinions, limiting '**su**', it is not necessary, right?

I also have a request: can someone answer the question in this topic? click: [_gvfs-fuse-daemon_]("http://ubuntuforums.org/showthread.php?p=12320011#post12320011") . I apologize, that I'm not waiting for an answer in correct topic, but it is very important. I know that I should not ask here, since my request is about something completely different. Nevertheless, thank you for your interest.

---

### Post by kleenex on 2013-01-20
Hi, I apologize for such a long time, but I thought about it. My last questions: 1) should I change access to **su** for root and users from **sudo** group (instead of **adm** group) with  e.g. [COLOR=Green]chown root:sudo /bin/su[/COLOR] command? 2) Leave it as it is by default; [COLOR=Green]root:root[COLOR=Black]? 3) ????

All apologies! Cheers!
[/COLOR][/COLOR]

---

### Post by Ms. Daisy on 2013-01-21
What exactly do you want to accomplish by changing access to su?

---

