---
title: "GDM logging on locally without entering password?"
date: 2005-01-26
forum: Server Platforms
---

### Post by darkfox on 2005-01-26
I am keen to use GDM to do something that I have done in KDM (I am trying to go with a Gnome-centric approach for a while):
  
 I want selected users to be able to log in locally via GDM without having to enter a password. Is this possible like it is via KDM?
  
  The GDM auto-login feature is not suitable because I need the solution to apply to a number of users.
  
 I know I can use 'passwd' to remove a user's password entirely, but given Ubuntu's sudo philosophy I think removing a user's password would be too slack from a security point of view.
  
  Thanks
  
  p.s. apologies if this post is in the wrong place - I couldn't decide if this was a desktop or a security issue

---

### Post by jdong on 2005-01-26
Yeah, it's possible. Look at the KDE Control Panel for the Display Manager (Login Screen) config options.

---

### Post by darkfox on 2005-01-26
JDong, maybe I didn't express myself well.  I don't have KDE installed, and I'm not trying to achieve this password-bypass in KDM:  I know KDM can do this.
 
 No, I'm trying to do this with GDM.  Are youy saying to me that I can use KDE's control panel to control GDM behaviour?  That just doesn't sound right...

---

### Post by mendicant on 2005-01-30
Look into the /etc/gdm/gdm.conf file.  There should also be a setup program somewhere (maybe via the gdm login screen?), which you can run manually--try gdmsetup.  Anyhow, in the config file, look at AutomaticLogin*, TimedLogin*.

---

### Post by Jad on 2005-01-30
[QUOTE=mendicant]Look into the /etc/gdm/gdm.conf file.  There should also be a setup program somewhere (maybe via the gdm login screen?), which you can run manually--try gdmsetup.  Anyhow, in the config file, look at AutomaticLogin*, TimedLogin*.[/QUOTE]
 Timed and auto login can be done for one user only

---

### Post by mendicant on 2005-01-30
That's what I get for not reading the entire original post...

---

### Post by darkfox on 2005-01-30
I know that in the past, buried in a GDM config file somewhere was a value UserNoPassword, which you used by specifying a list of users who didn't have to present passwords when logging on locally.  Unfortunately this no longer seems to work - either subsequent versions of GDM don't make use of it or the Ubuntu version has closed it down - I don't know which.
 
 Do you know if  UserNoPassword is still useable at all, or if there are alternative solutions?

---

### Post by christgod on 2005-02-07
Maybe this works, didn't check it though:
[http://mirror.hamakor.org.il/archives/linux-il/05-2004/10149.html](http://mirror.hamakor.org.il/archives/linux-il/05-2004/10149.html)


Edit: Yes it works!

---

### Post by Pluk on 2005-02-07
sudo gdmconfig, there you can set a user to autologin with at boot. no password required at boot for that user.

---

### Post by darkfox on 2005-02-08
[QUOTE=Pluk]sudo gdmconfig, there you can set a user to autologin with at boot. no password required at boot for that user.[/QUOTE]
 
 Please read the threads  - I have expressedly said that the goal is NOT to auto-logon, as this does not give the functionality that I seek.  I want multiple people to be able to log in locally without entering a password, and NOT have just one specific user get logged in automatically.

---

### Post by darkfox on 2005-02-08
Thank you so much christgod - the link you supplied does indeed work! Given that this seems to me like a fairly simple and common objective, and seeing as how I have not been able to find a solution till now, I thought I'd make a start on a mini-howto. The below instructions are for a debian-based system, and although it works in good conditions I am a newbie, so it may be full of holes. Perhaps someone with a bit more technical knowledge could take a look at this for me and see if it can be improved?
  
  (MINI) HOW TO ALLOW SPECIFIC USERS TO LOG ON VIA GDM LOCALLY WITHOUT ENTERING A PASSWORD
  
  [1] Why Bother?
 Well, partly because its just more convenient in some cases. If you are on a local network that is secure from remote access, where a machine is shared by multiple desktop users and where you trust some of them at least, why not let them have the benefits of their own account without the inconvenience of entering a password in GDM to log in? I know its no real hassle, but it is an extra step nonetheless. Anyway, choice is what we're all about, right? Partly also because Windows (and KDM!) lets you do this, and as a part of migrating folk over from Windows it is critical to no underestimate how important it is to minimise how much you take folk out of their familiarity zone. Even in small things like this. Exploration of the Linux way(s) can come after the initial terror subsides! If you use a user browser in GDM, this will allow the user to click on the picture representing them and they're in!
  
  [2] Have a word with PAM!
 PAM is the authentication model employed in Ubuntu. The first thing to do is to edit the PAM file that specifies how authentication should work with GDM. Open the file:
  $ sudo nano /etc/pam.d/gdm
 Add lines that specify a password is not required for the users who are listed in a file that you are going to make later on. The new line in the file example comes between the #start and #end comments, all the other lines were there anyway and remain untouched:
  ----------------------
     #%PAM-1.0
     auth    requisite    pam_nologin.so
     auth    required    pam_env.so
     # the line below has been added specifically to allow selected users to log in via GDM without a password
     # start
     auth sufficient pam_listfile.so item=user sense=allow file=/etc/X11/gdm/nopassusers.txt onerr=fail
     # end
     @include common-auth
     @include common-account
     session    required    pam_limits.so
     @include common-session
     @include common-password
  ----------------------
  
  [3] Tell PAM who to let in without a pass
  Go to this following location: /etc/X11/gdm/
  Make a new text file there called nopassusers.txt
  In this file, list the usernames of the users who can log in without entering a password.  Put each user on a new line.
  
 OK - that should be it. Like I say, I know this works but have no idea whether it is sensible. Please if you have knowledge contribute to making this a better howto!

---

### Post by Pluk on 2005-02-09
[QUOTE=darkfox]Please read the threads  - I have expressedly said that the goal is NOT to auto-logon, as this does not give the functionality that I seek.  I want multiple people to be able to log in locally without entering a password, and NOT have just one specific user get logged in automatically.[/QUOTE]


Oops and i thought i've read the OT ... must've forgotten to takemy pills... sorry

---

