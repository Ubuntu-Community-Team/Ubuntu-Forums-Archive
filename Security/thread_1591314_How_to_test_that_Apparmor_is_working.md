---
title: "How to test that Apparmor is working?"
date: 2010-10-09
forum: Security
---

### Post by DodgeV83 on 2010-10-09
So I activated the Firefox profile:

```
sudo aa-enforce /etc/apparmor.d/usr.bin.firefox
```

and restarted Firefox (even rebooted), but it doesn't seem to be working.  When I open Firefox I am able to perform a "Save Page As" in locations I shouldn't be able to, like my Desktop or Pictures folder.

The following command says the Firefox process is in enforce mode:

```
sudo apparmor_status
```

Of the following lines, the only directory which is "rw" is /Downloads, why am I still able to write to other places?

```
  # Default profile allows downloads to ~/Downloads and uploads from ~/Public
  owner @{HOME}/ r,
  owner @{HOME}/Public/ r,
  owner @{HOME}/Public/* r,
  owner @{HOME}/Downloads/ r,
  owner @{HOME}/Downloads/* rw,

```

OS: Ubuntu 10.10

Can someone with an active Firefox profile do this simple test for me?  Click File -> Save As and try to save somewhere the Apparmor profile shouldn't let you, and let me know the results.

---

### Post by rookcifer on 2010-10-09
I think someone else recently posted about the same issue on 10.10.  Not sure what the deal is.  A bug perhaps?

---

### Post by DodgeV83 on 2010-10-10
> **rookcifer said:**
> I think someone else recently posted about the same issue on 10.10.  Not sure what the deal is.  A bug perhaps?

I think that was me :-/

After installing Apparmor-notify, I can see in realtime that Apparmor is activated and working with my firefox install, but I can still "save-as" to random folders in my /home

Now I just need someone with 10.04 install and Apparmor installed to tell me if this is new behavior or not :)

---

### Post by Rubi1200 on 2010-10-10
The default AppArmor profile for Firefox is quite permissive.

You may want to consider trying the profile kindly provided by bodhi.zazen and see if that suits your needs better:
[http://bodhizazen.net/aa-profiles/bodhizazen/](http://bodhizazen.net/aa-profiles/bodhizazen/)

Also, read the AppArmor sticky to understand how to put the profile in complain mode for troubleshooting purposes.

Hope this helps.

---

### Post by rookcifer on 2010-10-10
> **Rubi1200 said:**
> The default AppArmor profile for Firefox is quite permissive.

You may want to consider trying the profile kindly provided by bodhi.zazen and see if that suits your needs better:
[http://bodhizazen.net/aa-profiles/bodhizazen/](http://bodhizazen.net/aa-profiles/bodhizazen/)

Also, read the AppArmor sticky to understand how to put the profile in complain mode for troubleshooting purposes.

Hope this helps.

Yeah, but his profile apparently does not allow writing to a directory he is writing to.  So something is wrong somewhere, and I doubt it's the profile.

OP, can you post the entire Maverick 10.10 Firefox profile here so that we can be sure the profile really does allow what you claim it shouldn't?

---

### Post by bodhi.zazen on 2010-10-10
I do not know why the default firefox profile allows you to write to files in you home directory, you should:

1. Report this as a bug.

2. Customize the profile to disallow this behaviour. You can use my 10.04 profile if you wish or I will try to look at the 10.10 profiles over the next few days.

---

### Post by rookcifer on 2010-10-10
I am upgrading my system to Maverick now, so I will take a look at the profile when it's finished.

---

### Post by DodgeV83 on 2010-10-10
I've had some luck explicitly denying things (Firefox said it didn't have the privileges to write to the folder), so I know Apparmor is working, but I don't think it's working as intended.  If a folder is set only to "r" and not "rw" this should mean Firefox can only read the folder and not write to the folder.  I should have to "deny" it.

I'll experiment a bit more before filing a bug.

---

### Post by rookcifer on 2010-10-10
OK, I just upgraded to Maverick and looked at the Firefox profile.  I figured out the problem.  If you look in the FF profile, you will see this line:
```

# Addons
#include <abstractions/ubuntu-browsers.d/firefox>
```

So, I followed the trail to that file and found another abstraction within this abstraction.  The abstraction in question is:

```
/etc/apparmor.d/abstractions/ubuntu-browsers.d/user-files
```

If you look in this file, you will see the following:

```

@{HOME}/ r,
@{HOME}/** r,
**owner @{HOME}/** w,**
owner @{HOME}/Desktop/** r,
```

So, what happened is Jamie put in an abstraction that lead to another abstraction that allows writing to any directory in /home.

So, the only way to fix it is to either modify the abstraction itself (not recommended since it might mess up other profiles) or to just specifically deny writing to certain directories in your /home directory.  A third option would be to create a FF profile from scratch.

---

### Post by DodgeV83 on 2010-10-10
> **rookcifer said:**
> OK, I just upgraded to Maverick and looked at the Firefox profile.  I figured out the problem.  If you look in the FF profile, you will see this line:
```

# Addons
#include <abstractions/ubuntu-browsers.d/firefox>
```

So, I followed the trail to that file and found another abstraction within this abstraction.  The abstraction in question is:

```
/etc/apparmor.d/abstractions/ubuntu-browsers.d/user-files
```

If you look in this file, you will see the following:

```

@{HOME}/ r,
@{HOME}/** r,
**owner @{HOME}/** w,**
owner @{HOME}/Desktop/** r,
```

So, what happened is Jamie put in an abstraction that lead to another abstraction that allows writing to any directory in /home.

So, the only way to fix it is to either modify the abstraction itself (not recommended since it might mess up other profiles) or to just specifically deny writing to certain directories in your /home directory.  A third option would be to create a FF profile from scratch.

Wow, that was fast!

Thanks :)

Problem solved

---

### Post by bodhi.zazen on 2010-10-11
If you are interested, I put my ff profile here:

[http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.10/](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.10/)

It is a bit restrictive perhaps, but it works for me. I *try* to stay as close as possible to the defaults, but I tighten up in $HOME a bit.

---

