---
title: "Least Privilege for Ubuntu 24.04 Standard User"
date: 2024-05-03
forum: Security
---

### Post by vbgf3 on 2024-05-03
Hi Everyone,


A standard user in Ubuntu does not automatically obey the least privilege principle.


You have to do 2 things:


a. Deny sudo. So that the user cannot use sudo to accomplish anything. In the admin account, run 'sudo visudo' and add in this line: ' user2 ALL=(ALL) !ALL ', replace the word user2 with the account name in question.


b. Gnome uses polkit to grant privileges, and it has additional action.id's which has to be controlled.
Create a file of any name inside /usr/share/polkit-1/rules.d/ . Include these lines:


polkit.addRule(function(action, subject) {
if ( ( action.id == "org.gtk.vfs.file-operations-helper" ||
action.id == "org.gtk.vfs.file-operations" ||
action.id == "org.freedesktop.policykit.exec"
)
&&
subject.user == "user2") {
return polkit.Result.NO; // Deny actions for user user2
}
});


This rule will forbid user2 from editing root owned configuration files, even if the admin password is compromised. And it will forbid user2 from accessing additional privileges.


If you wish to be extra cautious, just remove all the action.id lines and blanket ban user2 from doing anything that requires consulting polkit. This will ban things like configuring vpn's using Gnome > Settings for the account. And it will ban many other things, but surfing will still work. And, it will slow down Gnome. The primary activity of most users is to surf.

---

### Post by Tadaen_Sylvermane on 2024-05-03
> a. Deny sudo. So that the user cannot use sudo to accomplish anything.  In the admin account, run 'sudo visudo' and add in this line: ' user2  ALL=(ALL) !ALL ', replace the word user2 with the account name in  question.

Easier to just remove the user from the sudo group and adm groups. Make sure to set a root pw first else you lock yourself out. Same result. Much less screwing around.

---

### Post by vbgf3 on 2024-05-04
Gnome uses polkit in addition to sudo to control the things that can be done in Gnome. To see the list of action.id it additionally defined, look at the policy files in /usr/share/polkit-1/actions/ .  Some of those policies do indeed reference sudo. And removing a user from sudo works to a limited extent. But there are more actions in Gnome that are unique to Gnome. I was particularly disappointed by the way that Gnome handles modification of root owned config files. If you disabled sudo, Gnome will offer you a password prompt for the admin user. So if one knows the admin password, then one could type that in and still modify the file. In a company, passwords have a way of getting passed around, unbeknown to the admins of course. And then attackers could have lifted passwords from somewhere else, perhaps from another account, another system; via keyloggers etc. And compromised passwords are a major risk. And this I have to stop. 

Now one can say if the admin password is known, one can just log in to the admin account. To address that, I use 2FA. Gnome has support for YubiKeys and Google Authenticator. Yubikeys cost just $25 and is an offline 2FA method supported by Login via Google (PassKeys) and is available also to sudo;  and the cell phone Google Authenticator app is free. How to guide:  [https://support.yubico.com/hc/en-us/articles/360016649099-Ubuntu-Linux-Login-Guide-U2F](https://support.yubico.com/hc/en-us/articles/360016649099-Ubuntu-Linux-Login-Guide-U2F)

---

### Post by ajgreeny on 2024-05-04
I'm afraid you have lost me completely!
By default the only user on a standard Ubuntu system with membership of the sudo group  ie, able to run commands with raised privileges, is the first user set up at installation of the OS. Any other user does not have those abilities by default.

If any other user has the ability to run commands with sudo raised privileges ,they must have been given that membership of the sudo group by another user already in the group when the user was created.

I am not sure whether I am misunderstanding your meaning or if I am unaware of some abilities of users of gnome that I know nothing about as I can't stand gnome; I just find it unusable !

---

### Post by Tadaen_Sylvermane on 2024-05-04
> So if one knows the admin password, then one could type that in and  still modify the file. In a company, passwords have a way of getting  passed around, unbeknown to the admins of course.

While I'm not trying to start a debate this is why the Ubuntu way of sudo use is a bit dangerous. In a proper setup sudo should be for specific people to execute specific commands. Not for global root access which is how Ubuntu does it. The permissions capabilities in *nix are very granular. Anything can be easily disallowed with proper administration. A decent secret to anyone that doesn't need to know root password along with very clearly defined and implemented sudo rights for people based on their needs and nothing more is the right way to do it. I suppose the global root sudo user could be considered the root user in which case it works as long as no one else is a part of the primary sudo group. They should all be limited to the commands they need to accomplish their tasks and nothing more.

Ultimately no system is 100% impenetrable. But hacking around it when there are already ways to avoid what you are saying can happen is really just bad admin practices. Learn to do it the proper way. It's much easier to manage. You can manage it by groups rather than by each individual user. Your polkit file will get unmanageable real fast on a growing system.

---

### Post by vbgf3 on 2024-05-04
"[COLOR=#000000] Learn to do it the proper way. It's much easier to manage. ". Remember I am constrained by how Ubuntu is setup to work by default. My finding is that sudo does not entirely constrain Gnome in Ubuntu. Please do explain the proper way. I am all for a simpler way of managing things.


[/COLOR]

---

### Post by ian-weisser on 2024-05-04
> **vbgf3 said:**
> If you disabled sudo, Gnome will offer you a password prompt for the admin user. So if one knows the admin password, then one could type that in and still modify the file. In a company, passwords have a way of getting passed around, unbeknown to the admins of course.

I suppose you could ask Gnome to review their design.
Or you could address the password-passing problem. Folks do that when the current setup does not meet their needs. That's symptomatic of an admin or policy or leadership failure.

---

### Post by Tadaen_Sylvermane on 2024-05-04
While I'm thinking the polkit route is overkill this is a much simpler way to maintain it via that method.

For starters put any users who shouldn't be able to have any root of any kind in a specific group which you should create with a unique name and descriptive so it's easily picked out or remembered. Personally I'd make it a system group via ```
groupadd --system "$GROUPNAME"
``` so the UID's don't get separated from the GID's unless you already have a separate numbering for them. The users should NOT be in either the sudo or adm group.

```
polkit.addRule(function(action, subject) {    
    if (action.id == "org.freedesktop.login1.suspend" &&
        subject.isInGroup("users")) {
        return polkit.Result.YES;
    }
});
```

This is from the XFCE page on the Debian wiki. Use it as a model - [https://wiki.debian.org/Xfce](https://wiki.debian.org/Xfce)

```
subject.isInGroup("users"))
```

Replace the "users" with your custom group. Then you can block anyone in that group in one shot. This will solve your problem simply and allow it to grow naturally instead of you needing to modify it each time a new user is added. This should get you started.

---

### Post by vbgf3 on 2024-05-05
Thanks [COLOR=#000000]Tadaen. [/COLOR]

---

### Post by BBQdave on 2024-05-06
> **ajgreeny said:**
> I'm afraid you have lost me completely!
By default the only user on a standard Ubuntu system with membership of the sudo group  ie, able to run commands with raised privileges, is the first user set up at installation of the OS. 

...If any other user has the ability to run commands with sudo raised privileges ,they must have been given that membership of the sudo group by another user already in the group when the user was created.

Single user here, and I too am trying to understand the concern by the OP. Since I am the only user, I have the responsibility to act appropriately with system admin. If I add a user, and I make them admin level - it would be because I trust they are responsible with system admin.

Ultimately, it falls on the user with admin privileges to act appropriately with system administration. And (a whole other category) safe application use, such as a browser and safe sites to surf.

---

