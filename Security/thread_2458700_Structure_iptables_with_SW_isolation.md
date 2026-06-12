---
title: "Structure iptables with SW isolation"
date: 2021-03-02
forum: Security
---

### Post by lin32 on 2021-03-02
I'm trying to configure a machine in order to be able to do the followings:

1) Chrome (and all other User1 related programs in general, at least at the moment) is NOT allowed to access internet but only local network (used by User1)
2) Firefox (and only firefox, maybe additiona programs in the future) is allowed to access the internet (direct access) and is NOT allowed to access the local network (used by the same User1)
3) Ubuntu system and software updates are done through internet with redirection
4) Once User1 has logged in (with User1 password), he must be not asked again for any further password
5) User1 isn't root/admin and doesn't even know root/admin password

Any idea?
I've built a possible structure in iptables to achieve this using groups (e.g. Chrome > Group1 & Firefox > Group2), but how do I run both programs without being asked for a password (but at the same time keeping the system safe, meaning everything protected by password)?

Moreover, which are all groups responsible for system and software updates in Ubuntu?

---

### Post by TheFu on 2021-03-03
Ubuntu is a normal Linux system, so there's nothing special about it compared to other Linux systems you know except that direct login to root isn't allowed.

I can't answer all the questions. I would do things differently than your proposal using a web proxy server with user controls, linux containers, and perhaps a sandboxing tool like firejail. There are often 50-500 solutions to each problem on any Unix system.  Which answer is "best" depends on knowledge, skill, and future plans.

> 3) Ubuntu system and software updates are done through internet with redirection
I don't understand what this means.
>  4) Once User1 has logged in (with User1 password), he must be not asked again for any further password
If user1 (always use lowercase for usernames!!!!!), asks to do things that need elevated permissions, then a password will be requested. There isn't any way to stop that. Because their account doesn't have rights to access sudo, it won't matter.  But there are commands that someone might read in books which specifically ask for  a username and password. Those tools must be available on all desktop Linux systems or they will not boot.

The sudoers file allows configuration of specific access to run specific commands by specific users with specific options. To make life easier for normal users who need this access, I've always setup aliases that included the exact commands + options allowed.

>  Moreover, which are all groups responsible for system and software updates in Ubuntu? 
Just like every other Linux, that would be the root userid. On ubuntu, it is accessed using sudo.  Depending on the purpose of the system, you may want to enable automatic updates. On a desktop, that should be fine almost always.  I'd never do it on a server.

Learn more: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)

---

### Post by lin32 on 2021-03-03
Thank you for your response.

> I would do things differently than your proposal using a web proxy  server with user controls, linux containers, and perhaps a sandboxing  tool like firejail.
With *"web proxy server with user  controls"* do you mean an internal or external web server? The external  solution is not feasible since the place where operate changes, but even  a possible internal web server would seem to me a redundant layer and  at the end quite disproportionate to manage a routing of this type
With regard to Firejail, it was one of my initial options but to my knowledge it only allows limitations to specific programs, whereas in this case it would be a bit of the opposite: the whole operating system must be limited except for a single program (Firefox).

Maybe it would help to describe the current solution based on windows to better understand:
1) Operating system and programs are updated through Company-VPN (policy reasons)
2) Firefox can't access the local network, but has direct access to the internet (not via VPN otherwise you would get different IP and other issues)
3) Chrome can only access the local network (and not through VPN)
4) User1 (the name is fictitious, capitalization is just to try to make the post easier to read) has no administrative access + programs available in read-only mode (and once logged in, no other password is requested)
5) Firewall and everything else is configured at admin level

Until now I still didn't figure out a similar solution in Ubuntu (without asking again for password once logged in)

> Just like every other Linux, that would be the root userid. On ubuntu, it is accessed using sudo.  Depending on the purpose of the system, you may want to enable automatic updates. On a desktop, that should be fine almost always.  I'd never do it on a server.

Yes, clear to me. My question was related to better understand groups to redirect to VPN (please see point 1 above)

---

### Post by TheFu on 2021-03-03
> **lin32 said:**
> With *"web proxy server with user  controls"* do you mean an internal or external web server? The external  solution is not feasible since the place where operate changes, but even  a possible internal web server would seem to me a redundant layer and  at the end quite disproportionate to manage a routing of this type
Not a web server.  A web proxy - look up "squid".

> **lin32 said:**
> With regard to Firejail, it was one of my initial options but to my knowledge it only allows limitations to specific programs, whereas in this case it would be a bit of the opposite: the whole operating system must be limited except for a single program (Firefox).
Maybe you should consider placing the login inside a firejail? Then all child processes would be inside it too.  If you disallow network access, then no network access would be allowed.  I've not done this nor even looked to see if it was possible. It was just a thought.  A virtual machine could definitely accomplish this.

> **lin32 said:**
> Maybe it would help to describe the current solution based on windows to better understand:
Windows isn't Unix. They work entirely differently.

1) Patching is an admin role.  End users don't patch. There are many methods to handle this. I use scripts to patch 15 systems, but any devops tool like Ansible can be used. Local repos can be enforced, thus limiting which software is available by "bad admins" to install. Of course, any user can use their flash drive or internet to install a program under their HOME directory and run it from there. Normal users wouldn't know this, but any Unix person with 6 months of experience would.
2/3) Per application limitations are non-trivial. Having chrome/firefox with different network access seems like an arbitrary choice. Setup LAN-only access through the routing tables and only allow internet access when your web-proxy server is used. You can require logins for that, if you like and provide different groups/users with different external access.
4) User1 - If they don't have admin rights, then they don't have admin rights. I don't see the problem. If you won't want them to see programs in their menus, you have 2 choices.  Swap out the menuing system completely with one you control or remove the .desktop files which are magically discovered. Those are what create menus.  Just because a program isn't in the menu, that doesn't mean it isn't on the system and won't be run.  **The GUI is just another program. It isn't the OS.**  GUIs are full of lies.
5) Firewall and everything else is configured at admin level.  Firewall is controlled by admins. Normal users can't touch it.  "Everything else" isn't realistic.  Users have control over their personal settings and nothing you should do can change that.  OS settings are not included in that.  Mainly, users like to tweak their GUI settings.  You could wipe out their personal settings every day, if you like.  You'll have some very unhappy users. Expect a revolt.

> **lin32 said:**
> Until now I still didn't figure out a similar solution in Ubuntu (without asking again for password once logged in)
Windows isn't Unix. They work entirely differently.  Many things that are trivial in Unix are impossible in Windows. Similarly, many things that are impossible in Unix are trivial in Windows.  These are different OSes with extremely different philosophies.  Unix is about letting users have more power, not less.  By default any user can run a service on a Unix system. No special privileges needed, unless the listener wants to use a port under 1024 which is restricted.

Most of these things would be obvious if you setup a system, created the user1 account, then logged in under it. 20 minutes of effort.  Plus, many of the concerns seem to be DE/GUI related. Get specific about which GUI/DE you plan to use and someone else can help. I'm not much of a GUI user. Sorry.

---

### Post by lin32 on 2021-03-06
Suggested ways unfortunately doesn't seem to work.
Windows is not Unix is clear. Never claimed otherwise. I just reported what is done in Windows as an example (and I specified it!) to better explain in order to obtain the final result, despite the method (never said I was willing to obtain the same result using the same method used in Windows).
Anyway, I can understand something specific in Windows is done in a certain way and in Linux in an other way, but not being able to obtain the same result in Linux seems to me incredible. So, even if I don't want to use Windows, I'm still forced opt for it (at the moment) even if I'll keep searching, hoping to find a solution

---

### Post by TheFu on 2021-03-06
> **lin32 said:**
> Suggested ways unfortunately doesn't seem to work. 

Can you elaborate, please? What doesn't seem to work?  There where multiple suggestions.  Nobody can help without knowing exactly what was tried. 
Perhaps someone else can better explain the provided ideas than I can?  

Seems we have multiple barriers to understanding.  Windows-centric vs Unix-centric is the main issue. Hopefully, someone who speaks both can translate.

---

