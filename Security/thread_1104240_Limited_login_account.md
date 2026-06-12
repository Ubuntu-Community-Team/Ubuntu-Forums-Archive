---
title: "Limited login account"
date: 2009-03-23
forum: Security
---

### Post by BDNiner on 2009-03-23
Is there a way to severely limit a login account? I want to create an internet access PC. I already know how to remove extra programs and what not. My specific issues are: 

1) Is there a way to remove the log out option? All i want the user to be able to do is shutdown or restart the computer.

2) I also want to prevent anyone from locking the computer so removing that option would be helpful. 

3) Can i prevent a user from accessing any programs from the command line even though my admin login will still have access?

4) I would prefer to do this without a domain/polices. But any suggestions are welcome.

---

### Post by Bachstelze on 2009-03-23
Moved to Security Discussions.

---

### Post by LostMagix on 2009-03-23
You can do most of this with system/admin/users and groups

---

### Post by SunnyRabbiera on 2009-03-23
If you use Intrepid you can do most of this with the guest account, or create a new user with the add user applet.
The major hurdles that I dont think you can do is disable log out/lock, or prevent people from opening applications from the terminal.
With a limited account you can at the very least disable new users from installing applications and such, log out and lock are sort of standard in a linux system and disabling the terminal is practically impossible to do unless you remove the terminal manually from the menu's for each user.

---

### Post by BDNiner on 2009-03-23
Yeah but an inquisitive user can always press ctrl+alt+F1 and since the account is automatically set to login after 30 seconds then they have access to a terminal.

The only application that i want them to run is Firefox. Or whatever browser is decided upon. they don't need to run anything else. If I could make it boot right to an open firefox window that would be great.

---

### Post by bodhi.zazen on 2009-03-23
I think your bet bet is to look at KDE kiosk :

From there you can further restrict the guest with Apparmor.

[http://jriddell.org/programs/kiosk-article.html](http://jriddell.org/programs/kiosk-article.html)

[http://enterprise.kde.org/articles/kiosk-lp.php](http://enterprise.kde.org/articles/kiosk-lp.php)

From there apparmor can easily restrict what a guest can do.

---

### Post by SunnyRabbiera on 2009-03-23
> **BDNiner said:**
> Yeah but an inquisitive user can always press ctrl+alt+F1 and since the account is automatically set to login after 30 seconds then they have access to a terminal.

The only application that i want them to run is Firefox. Or whatever browser is decided upon. they don't need to run anything else. If I could make it boot right to an open firefox window that would be great.

I dont see the reasoning here of your restrictions, I mean its crazy insane to limit users to just 1 app.
Heck Firefox itself might cause security issues on its own more then any other app as its a web browser and can attract bad software.
Of course if firefox does indeed contract something it wont effect the whole system but still this sounds like a ultra paranoid setup.
I doubt your other users are going to contract anything by using any of the apps ubuntu installs by default.
If you disable users from root access and dont allow them to install 3rd party software then all should be fine.

---

### Post by BDNiner on 2009-03-23
It does sound paranoid but past experiences and the nature of the business that this is for lead to such restrictions. This machine is supposed to be stand alone and not interact with any other devices on the network. It is for web browsing only. 

I have seen some windows setups where the computer logs in and IE imediately opens, there is no start bar and when you press ctrl+alt+delete the only option you have is shutdown/restart. but this was done in a domain so polices can be set. since the PC i am trying to setup is stand alone then it makes it harder. I will look into kiosk mode. Seems like it was designed for internet cafes.

---

### Post by SunnyRabbiera on 2009-03-23
Well the computers will still be on a network if you just use a web browser, a web browsers very nature is to connect to a network after all...
Kiosk mode does come close though, but no OS is really safe when its plugged into the net.

---

### Post by bodhi.zazen on 2009-03-23
> **BDNiner said:**
> Yeah but an inquisitive user can always press ctrl+alt+F1 and since the account is automatically set to login after 30 seconds then they have access to a terminal.

The only application that i want them to run is Firefox. Or whatever browser is decided upon. they don't need to run anything else. If I could make it boot right to an open firefox window that would be great.

> **SunnyRabbiera said:**
> Well the computers will still be on a network if you just use a web browser, a web browsers very nature is to connect to a network after all...
Kiosk mode does come close though, but no OS is really safe when its plugged into the net.

As I said, this is where apparmor comes into play.

You can allow access to the system (/etc /bin /usr /tmp , etc) as much (or little) as necessary to run a desktop (x) and firefox.

Take a look at the sticky on apparmor and these resources :

[http://bodhizazen.net/aa-profiles/](http://bodhizazen.net/aa-profiles/)

In particular, look at jdong's jailbash ;)

---

### Post by BDNiner on 2009-03-23
> **bodhi.zazen said:**
> As I said, this is where apparmor comes into play.

You can allow access to the system (/etc /bin /usr /tmp , etc) as much (or little) as necessary to run a desktop (x) and firefox.

Take a look at the sticky on apparmor and these resources :

[http://bodhizazen.net/aa-profiles/](http://bodhizazen.net/aa-profiles/)

In particular, look at jdong's jailbash ;)

Thank you, this is very informative. It may accomplish what we are trying to do. Your topic called Introduction to AppArmor is very informative.

---

