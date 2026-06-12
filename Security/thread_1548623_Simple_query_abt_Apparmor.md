---
title: "Simple query abt Apparmor"
date: 2010-08-08
forum: Security
---

### Post by wacky_sung on 2010-08-08
Inspite i have read through the [sticky link]("http://ubuntuforums.org/showthread.php?t=1008906") but i have a query.

Example ,

If you have your firefox under enforce mode in apparmor,are you still able to install an update / addon to it to a newer version.

If not,how to disable the apparmor in firefox.Is it as below?

```
sudo /etc/AppArmor.d/usr.lib.firefox-3.0.4.firefox.sh stop
```

---

### Post by bodhi.zazen on 2010-08-08
Firefox should function normally, including addons, with the firefox profile enabled.

If needed, you put a profile into complain mode.

```
sudo aa-complain firefox
```

You may need the full path to the profile (i doubt it).

```
sudo aa-complain /etc/apparmor.d/usr.lib.firefox-3.0.4.firefox.sh
```

When a profile is in complain mode, it logs any potential denials but does not enforce them.

If the firefox profile is problematic (which I doubt) you would file a bug against it on Launchpad,

---

### Post by wacky_sung on 2010-08-08
I do know how to put the firefox under complain mode but my question is how to disable it instead of complain.Beside that,when it is under enforce mode in which am i able to install an updated version of firefox.Thank.

---

### Post by bodhi.zazen on 2010-08-08
> **wacky_sung said:**
> I do know how to put the firefox under complain mode but my question is how to disable it instead of complain.Beside that,when it is under enforce mode in which am i able to install an updated version of firefox.Thank.

If you update firefox, you will need to manually update the firefox profile. This is normally a trivial change, simply updating a few version numbers based on error messages.

You are going to have less problems if you put the profile into complain mode then disable it. Normally you would simply remove the profile altogether, ie ' sudo rm /etc/apparmor.d/usr.lib.firefox-3.0.4.firefox.sh ' , but if you do that apt-get is likely to complain about a missing file.

sudo service apparmor stop 

or

sudo /etc/init.d/apparmor stop 

disable all your apparmor profiles, probably not what you have in mind.

---

### Post by wacky_sung on 2010-08-08
> **bodhi.zazen said:**
> If you update firefox, you will need to manually update the firefox profile. This is normally a trivial change, simply updating a few version numbers based on error messages.

You are going to have less problems if you put the profile into complain mode then disable it. Normally you would simply remove the profile altogether, ie ' sudo rm /etc/apparmor.d/usr.lib.firefox-3.0.4.firefox.sh ' , but if you do that apt-get is likely to complain about a missing file.

sudo service apparmor stop 

or

sudo /etc/init.d/apparmor stop 

disable all your apparmor profiles, probably not what you have in mind.

How about just to disable the firefox profile alone instead of all the profile?What is the command?

Beside that,which mean that i gonna put it under complain each time before an installation of any updated newer version of firefox and redo for firefox profile in the apparmor.

---

### Post by bodhi.zazen on 2010-08-08
> **wacky_sung said:**
> How about just to disable the firefox profile alone instead of all the profile?What is the command?

Beside that,which mean that i gonna put it under complain each time before an installation of any updated newer version of firefox and redo for firefox profile in the apparmor.

There is no command to "disable" a profile. You either put the profile into complain mode or remove the configuration file.

Yes, every time you update firefox the apparmor profile will need to be updated. If you are ruing firefox from the repos , the firefox profile should update automatically.

As indicated, the update is trivial, updating the version numbers of firefox. Sometimes (usually) you can use wild cards

/usr/lib/firefox-*

---

### Post by rookcifer on 2010-08-08
> **wacky_sung said:**
> Inspite i have read through the [sticky link]("http://ubuntuforums.org/showthread.php?t=1008906") but i have a query.

Example ,

If you have your firefox under enforce mode in apparmor,are you still able to install an update / addon to it to a newer version.

If not,how to disable the apparmor in firefox.Is it as below?

```
sudo /etc/AppArmor.d/usr.lib.firefox-3.0.4.firefox.sh stop
```

Use a wildcard (*) inside the profile itself.  For instance, I have this line in my profile:

```
/usr/lib/firefox-3.*/** ixr,
```

Notice the asterisk (3.*) there.  This way I don't have to manually change the profile each time I upgrade to a new version (unless the version is 4).

---

### Post by wacky_sung on 2010-08-09
Before i actually proceed with my apparmor and i will very much appreciated if anybody with apparmor configure for their browser to test on an exploit and tell me the result of it.

This [link]("http://go2.wordpress.com/?id=725X1342&site=irsdl1.wordpress.com&url=http%3A%2F%2F0me.me%2Fdemo%2Fcrowzers%2Firsdl%2Fhalt.html&sref=http%3A%2F%2Firsdl1.wordpress.com%2F2010%2F06%2F30%2Fcrowzers-or-carzy-browsers%2F") will create a buffer overflow and crash firefox 3.6.6.It is still applicable to crash firefox 3.6.8 cause it to halt.

**[COLOR="Red"]Warning : Test it at your risk and i am not responsible for any damage done.[/COLOR]**

---

### Post by donato roque on 2010-08-09
If you are using Ubuntu 10.04, use the interactive tool for configuring apparmor, aa-logprof.  It offers "*" instead of version numbers, user just have to give assent to it. 

Put the profile in complain mode then use the application (firefox) then open a terminal and use aa-logprof.  Once the profile is updated you can end the session by cntl+Z.

---

### Post by wacky_sung on 2010-08-09
> **donato roque said:**
> If you are using Ubuntu 10.04, use the interactive tool for configuring apparmor, aa-logprof.  It offers "*" instead of version numbers, user just have to give assent to it. 

Put the profile in complain mode then use the application (firefox) then open a terminal and use aa-logprof.  Once the profile is updated you can end the session by cntl+Z.

Yes,i am using Ubuntu 10.04.By the way,what kinda command using the short key "cntl+Z".The crucial thing is that can apparmor guard against buffer overflow?I just need to verify that with an exploit otherwise it defeat the purpose for me if apparmor fail to prevent it.Probably someone can help me to test the link on the above thread.

---

### Post by bodhi.zazen on 2010-08-09
> **wacky_sung said:**
> Yes,i am using Ubuntu 10.04.By the way,what kinda command using the short key "cntl+Z".The crucial thing is that can apparmor guard against buffer overflow?I just need to verify that with an exploit otherwise it defeat the purpose for me if apparmor fail to prevent it.Probably someone can help me to test the link on the above thread.

You should test it yourself. Enable the firefox profile and test away.

---

### Post by wacky_sung on 2010-08-09
> **bodhi.zazen said:**
> You should test it yourself. Enable the firefox profile and test away.

Ah i did test it myself without any apparmor and it did really crash firefox 3.6.8.Apart from that,Google Chrome(5.0.375.125) has not much effect.The reason is that i do not wanna test apparmor now myself is because if apparmor cannot prevent it and it defeat the purpose for me to even run it.

[https://apparmor.wiki.kernel.org/index.php/Main_Page](https://apparmor.wiki.kernel.org/index.php/Main_Page)

```
AppArmor is an effective and easy-to-use Linux application security system. AppArmor proactively protects the operating system and applications from external or internal threats, even zero-day attacks, by enforcing good behavior and preventing even unknown application flaws from being exploited.
```

I will like to seek for volunteers who has apparmor configure on their browser otherwise that's fine for me.

---

