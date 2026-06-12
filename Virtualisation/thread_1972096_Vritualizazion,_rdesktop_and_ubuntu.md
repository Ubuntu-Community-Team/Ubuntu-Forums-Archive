---
title: "Vritualizazion, rdesktop and ubuntu"
date: 2012-05-03
forum: Virtualisation
---

### Post by redcats on 2012-05-03
Hi all,
I set up several virtual machines with XP vmware products.

Today I use the solution view by vmware for all my users to connect from a devon-it client to the virtual machine.

I would like to find another solution, cheaper solution.

I installed rdesktop on Ubuntu and it works very well. By cons it's just not possible fot my users every morning, start rdesktop and finally work.

So I thought about something else : Why not start by default Ubuntu in console mode and run the command "rdesktop-d domain-u user-en-k-ch -4 g 90% Destination" and thus allow my users to be directly connected to their Windows virtual machine :-) it would be great.

But as I'm a novice with linux, I don't know how to start directly ubuntu in console mode, and less how to execute a command after that.

That's why I ask you and I hope you will help be to find a solution. Someone has definitely already thought about it and maybe someone made it !

Thank you in advance

Regards
Dario

---

### Post by Dedoimedo on 2012-05-03
Would ssh or vnc work or must it be rdesktop?
Dedoimedo

---

### Post by redcats on 2012-05-04
Unfortunatly  no, only rdesktop :-(

---

### Post by newbie-user on 2012-05-04
You can set rdesktop to autostart when the user logs in

---

### Post by redcats on 2012-05-04
Thanks for your answer, but need rdesktop the x server to start or it's possible to run it in console mode ?

---

### Post by newbie-user on 2012-05-04
> rdesktop-d domain-u user-en-k-ch -4 g 90% Destination

You can have the users set up rdesktop to start up automatically when they log in. Go to System > Preferences > Startup Applications then add rdesktop with the command you posted above.

---

