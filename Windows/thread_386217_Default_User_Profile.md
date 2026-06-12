---
title: "Default User Profile"
date: 2007-03-16
forum: Windows
---

### Post by cyris| on 2007-03-16
Hey everyone,

I have a few windows xp pro machines that are connected to a samba domain. I've decided to use Local Profiles because some of these machines will be connecting over a VPN connection and id rather not be creating a heck load of traffic just transftering profiles.

What I've done is created my own Default Profile and made it mandatory by renaming the ntuser.dat to ntuser.man and replaced test machine. I've also set logon path = to nothing in my smb.conf which states use a local profile.

Whats happening is that user1 logins to the domain on the test machine for the first time, so no profile has been created. user1's profile is created by copying the Default Users profile.

My question to all your samba pros is that if user1's account is based of the Default Users Profile (which is mandatory) why do all my profile changes save the next time I login ? Example I create 5 open office documents and remove a few short cuts from user1's profile, logoff/login and all the documents are still their with the deleted short cuts gone :S

Thanks.

---

### Post by rickyjones on 2007-03-16
Did you check to see if the new profiles also have a renamed ntuser.dat file? It's possible that those changes didn't propogate correctly. 

-Richard

---

### Post by cyris| on 2007-03-17
Thanks for your reply. Some profiles have a ntuser.man and a ntuser.dat. My default profile only contains a ntuser.man file.

Its all weird to me, if new profiles are being based off of Default User then why are they getting a new ntuser.dat file ?

---

### Post by cyris| on 2007-03-19
No worries, I'm gonna stick with modifiable local profiles. Thanks for your help.

---

