---
title: "Unauthorised Remote Access"
date: 2013-08-09
forum: Security
---

### Post by colinoz on 2013-08-09
I recently installed Ubuntu 13.04. I did not know that Guest and Remote was "open" by default.

After a few sessions of use I got what at first I thought was a keyboard problem as anything I typed in a chat forum disappeared almost instantly. Then a message "Keep trying Colin" appeared above my cursor.

I did some research and disabled Remote and Guest. I also installed UFW (then Firestarter and Guarddog at different times to try and fix the remote access)

In later sessions (days apart after running Windows boots) I got similar things and then different folders started opening - I had lost control of the mouse. I figured that this was remote access again and I disconnected. It's happened a few times since and so I don't trust/use Ubuntu at the moment.

This is still happening and I won't use Ubuntu again until I fix the problem. As far as I know no damage to files (Ubuntu or my NTFS Win8 files has occurred).

Why does a firewall not stop this activity?
Has an unauthorised remote intruder installed a program that "phones home"? No one in my house would have installed anything or be the annoying intruder.

How can I fix the problem?

**ALL ADVICE WILL BE VERY GRATEFULLY APPRECIATED!!!!!!!!!!!!!!!!!**

Thanks
COLIN

---

### Post by SlugSlug on 2013-08-09
You should really reinstall. The attacker could have installed anything / added his own account

---

### Post by SeijiSensei on 2013-08-09
Do you mean that the installation created a user called "guest" and another called "remote?"  Is this something unique to vanilla Ubuntu?  I use Kubuntu, and there is no "guest" or "remote" user in my /etc/passwd.

Perhaps this problem is with the chat program you are using?  Is this a server-based program, where all the messages are routed through a central server rather like Twitter, or does it actually allow people to connect directly to your machine?  I would never use a program like that without some serious investigation into its security.

Not only should you reinstall Linux, but if you have a Windows partition mounted into the Linux filesystem, I'd be concerned about the integrity of your Windows installation as well.  At a minimum run a complete virus scan in Windows.

---

### Post by cariboo on 2013-08-09
A vanilla install of Ubuntu has the guest account enabled, and of course you have to access it from lightdm, there is also an option to allow a user to login to a remote computer, both can be easily hidden using the following command:

sudo /usr/lib/lightdm/lightdm-set-defaults --hide-users true

For more info on modifying lightdm, have a look at this blog post:

[http://www.mattfischer.com/blog/?p=343](http://www.mattfischer.com/blog/?p=343)

---

### Post by colinoz on 2013-08-10
Thanks for your responses.
I haven't had any problems or intrusions in Win8.

I read the lightdm article - but can this be used to stop remote logins like I am experiencing?

I may try booting from a USB for a while as reinstalling will be a bit of a pain and I'm pressed for time.

I'll await further responses.

Thanks everyone
COLIN

---

### Post by cariboo on 2013-08-10
> **colinoz said:**
> Thanks for your responses.
I haven't had any problems or intrusions in Win8.

I read the lightdm article - but can this be used to stop remote logins like I am experiencing?

I may try booting from a USB for a while as reinstalling will be a bit of a pain and I'm pressed for time.

I'll await further responses.

Thanks everyone
COLIN

I'd suggest you check and make sure that vino, the remote access server isn't running. Open a terminal and type the following command:

```
vino-preferences
```

and make sure desktop sharing isn't enabled.

---

### Post by colinoz on 2013-08-10
[COLOR=#000000][COLOR=#DD4814][COLOR=#990303]Hi [cariboo907]("http://ubuntuforums.org/member.php?u=77104")[/COLOR][/COLOR] 

I checked 
[FONT=Ubuntu Mono]vino-preferences. Sharing was allowed - possibly without password!

I've turned all off and set a VERY hard password. I hope this will stop the problem.

I'll turn off wi-fi when I leave the screen.

Do you think this external user got in when I had the default settings on setup and changed this? Or can it be a problem for all new installs?

Thanks for the response. I'll keep posting if I have more break-ins! I'll give some feedback if I have none in a week.

COLIN[/FONT][/COLOR]
.

---

### Post by cariboo on 2013-08-11
The remote desktop client, is one of the most easiest ways for anyone to get into the system. There are countless threads in this sub-forum from people that have started the service, and then set it for no, or a very easy password. If you don't need to access your desktop remotely, don't turn the service on. 

If you want to access files on your desktop system, use either samba, or sftp.

---

### Post by colinoz on 2013-08-29
I haven't used Ubuntu for a while, but today's use seems OK so far.

Whilst I'm an experienced WIN user, a less experienced user installing Ubuntu may have not solved the issue so easily and may have suffered some damage.

The default install for Ubuntu seems a little insecure and MOST new users would not want these features enabled. Perhaps an inexperienced user may need an expert to login remotely to fix a problem, but this is feature available on install is a high security price to pay for this *POSSIBLE* need!

Thank you everyone for your help!
COLIN

---

### Post by mr-woof on 2013-08-29
I always thought that vino was disabled by default?

---

### Post by Irihapeti on 2013-08-29
Vino is disabled by default, but it seems that it's perilously easy to enable it without realising what you're doing &#8211; going by what I've seen in this forum over the years.

Some of us have asked the devs to not ship Ubuntu with it installed, but to no avail. I wonder what would have to happen for them to change their minds. One of their close relatives getting compromised?

---

### Post by mr-woof on 2013-08-29
I thought so, I agree it could do with being removed from the default install.

---

### Post by SeijiSensei on 2013-08-29
> **mr-woof said:**
> I thought so, I agree it could do with being removed from the default install.

I don't see any vino binary in my Kubuntu 13.04 installation, just some header files for the kernel, and a default vino-preferences.desktop file.  I guess the Kubuntu packagers have a different view about security than the vanilla Ubuntu packagers.

I've never liked the default of world-readable home directories either.

---

