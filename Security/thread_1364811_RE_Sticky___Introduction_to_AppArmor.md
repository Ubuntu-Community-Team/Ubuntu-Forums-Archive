---
title: "RE: Sticky:   Introduction to AppArmor"
date: 2009-12-26
forum: Security
---

### Post by JohnnyJonJon on 2009-12-26
It is a great thread, well written and full of very useful information, thank you.

I'm just left with a few questions.

1) What is the default setup for 9.10?  The thread only talks about 9.04.

2) If I update a software package do I need a new policy? i.e. firefox 2 -> 3

3) Do I have to turn on apparmor? I don't see it in the process list.

Sorry if these are answered and I just didn't get it :???:

---

### Post by rookcifer on 2009-12-26
> **JohnnyJonJon said:**
> It is a great thread, well written and full of very useful information, thank you.

I'm just left with a few questions.

1) What is the default setup for 9.10?  The thread only talks about 9.04.

About the same.  9.10 now has a profile for Firefox that is disabled, but you can easily enable it.
> 
2) If I update a software package do I need a new policy? i.e. firefox 2 -> 3

Not usually.  If it's a minor upgrade, say 3.5.5 to 3.5.6, it will work seamlessly.  If it is a major number revision (say 3.x to 4.x), it would probably be wise to write a new policy.

> 3) Do I have to turn on apparmor? I don't see it in the process list.

It should already be on.  However, there are only a few profiles enabled.  You will need to install the extra profiles or create some yourself.

---

### Post by q.dinar on 2009-12-27
hello.
i add something to these.
to 1st question and adding to answer to 3rd question: you can check/know out which profiles work with "sudo apparmor_status".
to 2nd question: only some program file names change by version, one of them is firefox, but it is possible to write "*" instead of changing number in profile file content[ in place] where program file and path name is written at external side of and before main "{}" brackets of profile.
to 3rd question: appamor is part of kernel as i know. kernel module. kernel is not shown in process list, as i know. by the way, i do not know why it is not shown.

---

### Post by bodhi.zazen on 2009-12-27
You can see the status of apparmor with :

```
sudo aa-status
```

By default most if not all the profiles are in complain mode.

I would advise you do two things :

```
sudo apt-get install apparmor-profiles
```

This will install additional profiles :twisted:

Then enable them =)

```
sudo aa-enforce /etc/apparmor.d/*
```

---

### Post by CharlesA on 2009-12-27
Is there any point to adding more aa profiles if you aren't running a desktop gui?

Right now I've got 4 profiles in enforce mode.

---

### Post by JohnnyJonJon on 2009-12-27
> **rookcifer said:**
> About the same.  9.10 now has a profile for Firefox that is disabled, but you can easily enable it.

Excellent thank you.  Firefox and aMSN are my biggest concern.

> Not usually.  If it's a minor upgrade, say 3.5.5 to 3.5.6, it will work seamlessly.  If it is a major number revision (say 3.x to 4.x), it would probably be wise to write a new policy.ok

> It should already be on.  However, there are only a few profiles enabled.  You will need to install the extra profiles or create some yourself.right, thank you.  my task for the day will be one for aMSN :)

---

### Post by JohnnyJonJon on 2009-12-27
> **q.dinar said:**
> hello.
i add something to these.
to 1st question and adding to answer to 3rd question: you can check/know out which profiles work with "sudo apparmor_status".
to 2nd question: only some program file names change by version, one of them is firefox, but it is possible to write "*" instead of changing number in profile file content[ in place] where program file and path name is written at external side of and before main "{}" brackets of profile.
to 3rd question: appamor is part of kernel as i know. kernel module. kernel is not shown in process list, as i know. by the way, i do not know why it is not shown.

Ah yes, the wild card=D>

A module #-oof course!  Thank you!

---

### Post by JohnnyJonJon on 2009-12-27
> **bodhi.zazen said:**
> You can see the status of apparmor with :

```
sudo aa-status
```By default most if not all the profiles are in complain mode.
Very nice :)

> I would advise you do two things :

```
sudo apt-get install apparmor-profiles
```This will install additional profiles :twisted:

Then enable them =)

```
sudo aa-enforce /etc/apparmor.d/*
```Done and done \\:D/

Thank you all for the help O:)

Is it possible to get an aa profile in the deb package that gets enabled as part of the install process?  That is something I would really like to happen :smile:

---

### Post by JohnnyJonJon on 2009-12-27
> **CharlesA said:**
> Is there any point to adding more aa profiles if you aren't running a desktop gui?

Right now I've got 4 profiles in enforce mode.

I think all internet programs are at risk of the man-in-the-middle attack, so I would say yes to anything that receives packets off the net ;)

---

### Post by q.dinar on 2009-12-27
also there are some profiles in /usr/share/doc/apparmor-profiles/extras/ .

---

### Post by bodhi.zazen on 2009-12-27
> **JohnnyJonJon said:**
> Is it possible to get an aa profile in the deb package that gets enabled as part of the install process?  That is something I would really like to happen :smile:

Some packages, like firefox, have aa profiles. They are in various places, I think apparmor-profiles

Those profiles all are in complain mode by default, as with the firewall, the default behavior is to be permissive.

Since apparmor can cause problems, I do not think this will change any time soon.

For other apps you have to write your own profile..

 If you would like to see what apparmor can do, try zenix.

[http://zenix-os.net/index.php?nav=features](http://zenix-os.net/index.php?nav=features)

all network apps have a profile.

the guest account has a password of "guest" and is confined by apparmor.

---

