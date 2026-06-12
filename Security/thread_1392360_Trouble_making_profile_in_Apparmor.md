---
title: "Trouble making profile in Apparmor"
date: 2010-01-28
forum: Security
---

### Post by projectX on 2010-01-28
ok, I've never really had any issues before in making profiles for apparmor but I keep getting the same thing over and over again, no matter what I do. Here is what I get in my terminal:

> 
mjl08@michael:~$ sudo genprof xchat

Please start the application to be profiled in 
another window and exercise its functionality now.

Once completed, select the "Scan" button below in 
order to scan the system logs for AppArmor events.  

For each AppArmor event, you will be given the  
opportunity to choose whether the access should be  
allowed or denied.

Profiling: /usr/bin/xchat

[(S)can system log for SubDomain events] / (F)inish
Reading log entries from /var/log/messages.
Updating AppArmor profiles in /etc/apparmor.d.

Create New User?

(Y)es / [(N)o]
Username: michael
Password: *****
Email Addr: ********@Gmail.com

Save Configuration? 

[(Y)es] / (N)o

Login Error
RPC::XML::Client::send_request: HTTP server error: Not Found

Create New User?

(Y)es / [(N)o]


I have also tried to manually edit the file to my liking but don't get any access to it. I've also tried to remake the file but still get the same thing that is posted in the top. I know this is all newbe questions but I haven't used Linux in some time, so I am getting back to refreshing myself.

I've looked all over this board as well as google to be able to find out what is going on (and trust me, I've searched everything before posting). Here is also the file I am trying to update:

> 
# Last Modified: Wed Jan 27 04:14:50 2010
#include <tunables/global>

/usr/bin/xchat flags=(complain) {
  #include <abstractions/base>

}


---

### Post by rookcifer on 2010-01-28
I have the same problem.  I have told the main AppArmor developers about this in IRC and they just tell me "AppArmor's logprof has some issues right now."  They never say if/when they will be fixed.  In Jaunty logprof worked fine for me, but in Karmic it has a mind of its own.  Sometimes it will pick up the log errors and sometimes it ignores them.  Also, as you said, sometimes it asks you the same questions over and over again.

So, about the only thing you can do is just look at your log files manually and create the profiles by hand.

---

### Post by projectX on 2010-01-28
Thanks for the reply and that pretty much sums it right up. Wonder when a update will be coming out for it so it makes things easier lol. I hate to ask, but can you remind me on how to make them by hand again... I tried to make them once before but it denied my access to have them moved to the folder or do I have to point them to the home folder and stash them there.

---

### Post by rookcifer on 2010-01-28
> **projectX said:**
> Thanks for the reply and that pretty much sums it right up. Wonder when a update will be coming out for it so it makes things easier lol. I hate to ask, but can you remind me on how to make them by hand again... I tried to make them once before but it denied my access to have them moved to the folder or do I have to point them to the home folder and stash them there.

Just go through your AppArmor log files (which are probably in /var/log/messages unless you have installed auditd).  Pick out the AppArmor log messages there, and you will see what is being denied and why it's being denied.  Then just go to the profile in question which is located in /etc/apparmor.d and modify the rule by hand.

For example, here is what a denial log will look like:
```

type=APPARMOR_DENIED msg=audit(1264205487.530:84): operation="exec" pid=21849 parent=16618 profile="/usr/lib/firefox-3.5.*/firefox.sh" requested_mask="::x" denied_mask="::x" fsuid=1000 ouid=0 name="/usr/lib/openoffice/program/soffice" 
```

What this is saying is that AppArmor denied firefox execution of /usr/lib/openoffice/program/soffice.  So, basically, Firefox was wanting to open soffice for some reason and was denied.  To rectify this, I would go to /etc/apparmor.d, open up my firefox profile with nano and add the following line:

```
/usr/lib/openoffice/program/soffice rix,
```

The "rix" means to give it read and execute permissions while inheriting the security profile of Firefox.

---

### Post by projectX on 2010-01-28
Alright, found it and thank you for the help. Much appreciated.

---

### Post by bodhi.zazen on 2010-01-29
When using logprof, just say no to creating a new user or contacting the repositories.

These functions are hold overs from when apparmor was developed on SUSE.

---

### Post by projectX on 2010-01-29
> **bodhi.zazen said:**
> When using logprof, just say no to creating a new user or contacting the repositories.

These functions are hold overs from when apparmor was developed on SUSE.

Thanks for the reply and I've just tried those but it still wants me to make a new user even when I say no to either or them. I can post an example if needed.

---

### Post by bodhi.zazen on 2010-01-29
> **projectX said:**
> Thanks for the reply and I've just tried those but it still wants me to make a new user even when I say no to either or them. I can post an example if needed.

You should probably file a bug report on launchpad.

---

### Post by projectX on 2010-01-29
Going to go and do that right now.

---

