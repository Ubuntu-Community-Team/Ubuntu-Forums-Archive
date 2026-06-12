---
title: "Users turning up in login 'list' that are /bin/false"
date: 2012-04-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by shadowfirebird on 2012-04-13
For NFS-y reasons I added a couple of users and set them as non-login (shell is /bin/false).   However they are turning up in the LightDM login list, and the Unity "Switch Users" dialogue.  

Anyone got any ideas how I can fix this?

---

### Post by bluenova on 2012-04-13
Set the UID below 1000

I have an admin user that I use purely for fresh installs so's not to mess with my own account. Once setup I set the UID of that user to 999 to remove it from the login screen.

---

### Post by shadowfirebird on 2012-04-13
> **bluenova said:**
> Set the UID below 1000

I have an admin user that I use purely for fresh installs so's not to mess with my own account. Once setup I set the UID of that user to 999 to remove it from the login screen.

I can't do that.  The whole point of having these users is that their UID has to match the UID on the server -- where they *can* log in.

I guess I'll just have to raise it as a bug and live with it for now.

---

### Post by haqking on 2012-04-13
> **shadowfirebird said:**
> I can't do that.  The whole point of having these users is that their UID has to match the UID on the server -- where they *can* log in.

I guess I'll just have to raise it as a bug and live with it for now.

just cos the UID is less than 1000 and it doesnt appear at login doesnt mean you cant login with it.

you can login with root but its UID of 0 and doesnt appear ;-)

Edit. actually i just remember isnt there an issue with the "other" login in 12.04 ? I havent used it so cant tell you for sure on that but i think there may be an issue.
Peace

---

### Post by cariboo on 2012-04-13
The other login  is a totally different problem to the one shadowfirebird is suffering from. If I remember correctly lightdm is hard coded to show any UID's above 1000. I'd suggest that if you don't like the behavior and can't change the UID's on the server, that you use gdm instead.

---

### Post by haqking on 2012-04-13
> **cariboo907 said:**
> The other login  is a totally different problem to the one shadowfirebird is suffering from. If I remember correctly lightdm is hard coded to show any UID's above 1000. I'd suggest that if you don't like the behavior and can't change the UID's on the server, that you use gdm instead.

yeah but what i was saying was if he gave the UID lower than 1000 it wont show up, but he still wants users to be able to logon with the account, which you usuualy can, except i heard there was an issue showing the "other" logon in 12.04 ?

in other words how do you show the "other" logon in 12.04 therefore making it possible to logon with UID below 1000 which wont be shown ?

Cheers

---

