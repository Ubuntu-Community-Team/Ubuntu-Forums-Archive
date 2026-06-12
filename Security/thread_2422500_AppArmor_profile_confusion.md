---
title: "AppArmor profile confusion"
date: 2019-07-08
forum: Security
---

### Post by craig-merchant on 2019-07-08
I'm new to AppArmor.  I started with this tutorial and tried to build a profile for the Splunk daemon:

[https://tutorials.ubuntu.com/tutorial/beginning-apparmor-profile-development#0](https://tutorials.ubuntu.com/tutorial/beginning-apparmor-profile-development#0)

I used aa-easyprof to create an empty profile and copy it to /etc/apparmor.d.  I then loaded it into the kernel.

I then used "aa-complain /opt/splunk/bin/splunkd" to put the profile in complain mode and then performed a bunch of actions like downloading apps, enabling inputs, etc.

When I run "[COLOR=#333333][FONT=&quot]aa[/FONT][/COLOR][COLOR=#333333][FONT=&quot]-[/FONT][/COLOR][COLOR=#333333][FONT=&quot]notify [/FONT][/COLOR][COLOR=#333333][FONT=&quot]-[/FONT][/COLOR][COLOR=#333333][FONT=&quot]s [/FONT][/COLOR][COLOR=#333333][FONT=&quot]1[/FONT][/COLOR][COLOR=#333333][FONT=&quot] [/FONT][/COLOR][COLOR=#333333][FONT=&quot]-[/FONT][/COLOR][COLOR=#333333][FONT=&quot]v", I see hundreds of messages of complaints about splunkd doing something or other.  

But when I ran aa-logprof, it only prompted me for a single permission and then asked me to save it.  I did so many different things in my testing that it is kind of surprising that it only asked permission about one.  When I saved the profile and restarted apparmor, when I run aa-status, I see over a hundred policies that look like:
[/FONT][/COLOR]
   /opt/splunk/bin/splunkd
   /opt/splunk/bin/splunkd//null-/bin/dash
   /opt/splunk/bin/splunkd//null-/bin/dash//null-/opt/splunk/bin/python
   /opt/splunk/bin/splunkd//null-/bin/dash//null-/opt/splunk/bin/python//null-/opt/splunk/bin/splunkd
   /opt/splunk/bin/splunkd//null-/opt/splunk/bin/mongod
   /opt/splunk/bin/splunkd//null-/opt/splunk/bin/python
   /opt/splunk/bin/splunkd//null-/opt/splunk/bin/python//null-/opt/splunk/bin/btool
   /opt/splunk/bin/splunkd//null-/opt/splunk/bin/python//null-/opt/splunk/bin/btool//null-/opt/splunk/bin/splunkd
   /opt/splunk/bin/splunkd//null-/opt/splunk/bin/python//null-/opt/splunk/bin/jsmin
   /opt/splunk/bin/splunkd//null-/opt/splunk/bin/python//null-/opt/splunk/bin/splunkd
   /opt/splunk/bin/splunkd//null-/opt/splunk/bin/splunk

But when I edit /etc/apparmor.d/opt.splunk.bin.splunkd, the policy looks very minimal:


#include <tunables/global>


# vim:syntax=apparmor
# AppArmor policy for splunkd
# ###AUTHOR###
# ###COPYRIGHT###
# ###COMMENT###
# No template variables specified




/opt/splunk/bin/splunkd flags=(complain) {
  #include <abstractions/base>
  #include <abstractions/lxc/container-base>


}

I'm an apparmor noob...  I don't understand how aa-status shows hundreds of policies, but there don't appear to be any config files in /etc/apparmor.d that correspond to them and the policy for splunkd is pretty much empty.

What am I not getting...?

First post to the community.  Thanks in advance.

C

---

