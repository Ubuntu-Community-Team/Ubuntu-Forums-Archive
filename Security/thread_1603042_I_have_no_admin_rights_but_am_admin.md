---
title: "I have no admin rights but am admin"
date: 2010-10-22
forum: Security
---

### Post by NimbusII on 2010-10-22
Sorry for the strange title but this is hard to describe....

I am only user on this ubuntu 10.10 install... 
I have admin rights but when I try to change some settings via Ubuntu tweak unlock  or alter user and groups via advanced tab I never get the option to enter my password...
I have added a new user `tempuser` via safe mode and this user is administrator too but everything works fine from this user.. 

Results from $ grep admin /etc/group
lpadmin:105:heath,tempuser
admin:119:firstuser,tempuser,heath

Results from groups
admin adm dialout fax cdrom floppy tape audio dip video plugdev fuse lpadmin sambashare

I am thinking of making a fresh install if i cant sort this but would like to fix if poss... Sorry i`m a little vague but ask any questions...

Thanks
Heath

---

### Post by CharlesA on 2010-10-22
Does it let you change users and groups without using Ubuntu Tweak?

There should be an "unlock" button available in the Users and Groups applet if you are logged in locally.

---

### Post by NimbusII on 2010-10-22
In users and groups i get no response from the advanced button.. 
When using ubuntu tweak the unlock button gives no response. I am using the latest version.

---

### Post by CharlesA on 2010-10-22
So the other user is able to access that area just fine?

Are you able to use sudo, by chance?

---

### Post by sisco311 on 2010-10-22
> **NimbusII said:**
> In users and groups i get no response from the advanced button.. 
When using ubuntu tweak the unlock button gives no response. I am using the latest version.

What's the output of:
```
pgrep -lf polkit
```?

---

### Post by NimbusII on 2010-10-22
> **sisco311 said:**
> What's the output of:
```
pgrep -lf polkit
```?

Hi the output is 
1265 /usr/lib/policykit-1/polkitd

---

### Post by NimbusII on 2010-10-22
> **CharlesA said:**
> So the other user is able to access that area just fine?

Yes no problem from other user login

Are you able to use sudo, by chance?

If I sudo Ubuntu-tweak all settings are available including unlock!

---

### Post by CharlesA on 2010-10-22
I mean: Are you able to use sudo from a terminal and it lets you.

Sounds like that works.

---

### Post by NimbusII on 2010-10-22
> **CharlesA said:**
> I mean: Are you able to use sudo from a terminal and it lets you.

Sounds like that works.

Yes Sudo from terminal works fine.....

---

### Post by sisco311 on 2010-10-22
It seams you somehow removed the policykit authentication agent from the auto start applications. Run the agent:
```
/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1 &
disown
```
then test it if it works:
```
pkexec echo
```
If the authentication window pops up, close it and add the agent to the auto-start applications:
```
mkdir -p ~/.config/autostart/
cp /etc/xdg/autostart/polkit-gnome-authentication-agent-1.desktop ~/.config/autostart/
```
Log out and log back in to check if the agent starts.

---

### Post by NimbusII on 2010-10-22
> **sisco311 said:**
> It seams you somehow removed the policykit authentication agent from the auto-started applications. Run the agent:
```
/polkit-gnome-authentication-agent-1 &
disown
```then test it if it works:
```
pkexec echo
```If the authentication window pops up, close it and add the agent to the auto-started applications:
```
mkdir -p ~/.config/autostart/
cp /etc/xdg/autostart/polkit-gnome-authentication-agent-1.desktop ~/.config/autostart/
```Log out and log back in to check if the agent starts.

I do not have a /usr/lib/polkit-gnome.........nearest i have is polkit-1:???: this is with show hidden files.....

---

### Post by sisco311 on 2010-10-22
> **NimbusII said:**
> I do not have a /usr/lib/polkit-gnome.........nearest i have is polkit-1:???: this is with show hidden files.....

Oh, sorry, (in Ubuntu :) ) it's:
```
/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1 &
```

---

### Post by NimbusII on 2010-10-22
Fantastic.......thats sorted it..... thanks very much for your help...... much appreciated....

---

### Post by sisco311 on 2010-10-22
You are welcome!

You can mark this thread as **[SOLVED]** by selecting "Mark this thread as Solved" from the "[COLOR="Red"]Thread Tools[/COLOR]" menu. It's at the top of the page.

---

### Post by lisantir5 on 2010-10-24
I had the same problem with my new 10.10 computer when using both "User and Groups" and Ubuntu-Tweak.  I noticed my User account type is "Custom" and has admin privileges.  My 10.04 Lucid computer had the same settings and does not have this problem so I suspect it is a 10.10 problem.  Since I am an avid user and not a "techie" I appreciate the quick fix.  I also tried adding a "system" user (adduser) from the CLI but the user never showed up in the "User and Groups" gui so thanks to NimbusII for the "Safe Mode" tip. I guess the safe bet would be to have 3 accounts, one "user", one "custom admin" and one regular "admin".

---

### Post by tophousetim on 2010-10-25
I've just had this problem with 10.04 and used the policy kit fix described here to put the priviledges right. Although I have no idea how things got tangled. Thanks sisco311.

---

