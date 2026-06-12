---
title: "Sudo to delegate permission from non-root user to another non-root user"
date: 2012-04-05
forum: Security
---

### Post by canar on 2012-04-05
[FONT=Arial][SIZE=2]I've been through many threads before i decide to create a separate thread.
I can't really find the solution to my (simple) problem.

Here's what I'm trying to achieve:
As "canar" user I want to run a command, let's say "/opt/ocaml/bin/ocaml" as "duck" user.

The only to achieve this is to give "canar" user root permission in sudoers, see below: [/SIZE][/FONT][FONT=Courier New]
 [/FONT][FONT=Courier New][COLOR=Blue]Host_Alias      LAB = [/COLOR][/FONT][FONT=Courier New][COLOR=Blue]linuxbox
  [/COLOR][/FONT][FONT=Courier New][COLOR=Blue]User_Alias      LABTRUSTED = canar
  [/COLOR][/FONT][FONT=Courier New][COLOR=Blue]Cmnd_Alias      LABADMIN = /bin/bash, /bin/su, /bin
  [/COLOR][/FONT][FONT=Courier New][COLOR=Blue]LABTRUSTED       LAB=(ALL) NOPASSWD: LABADMIN[/COLOR]

[FONT=Arial][SIZE=2] And run any command:[/SIZE][/FONT][/FONT][FONT=Arial][SIZE=2]
 [/SIZE][/FONT][FONT=Arial][SIZE=2]canar@linuxbox$ sudo -i -u duck  'id'


[/SIZE][/FONT]  [FONT=Arial][SIZE=2]But basically, this is a huge security hole since canar can run whatever he wants as anyone (including root)
[/SIZE][/FONT][FONT=Arial][SIZE=2]I want to restrict canar user to be able to login as duck user (or as anyone from a given group) without providing root access

**Edit: **[/SIZE][/FONT]**[FONT=Arial][SIZE=2] want to restrict canar user to be able to run an identified command as duck user (or as anyone from a given group) [COLOR=Red]without [/COLOR]providing root access[/SIZE][/FONT]**
[FONT=Arial][SIZE=2] 
Any help would be welcome!   [/SIZE][/FONT][FONT=Arial][SIZE=2]
~canar[/SIZE][/FONT]

---

### Post by papibe on 2012-04-05
Hi canar. Welcome to the forums!

If what you want to run is an binary file (not an script), you may solve the problem using setuid and setgid bits. When a program with those bits set runs, it will have the same permissions as the owner of the file being executed.

Read more about it [here]("http://www.zzee.com/solutions/linux-permissions.shtml#setuid").

Hope that helps, and tell is how it goes.
Regards.

---

### Post by canar on 2012-04-05
hi papibe,
thanks for the warm welcome and the answer.

however, i don't want to setuid nor setguid on a file, instead i want to leverage sudo.
Is it doable? if so, how?

---

### Post by canar on 2012-04-06
Bump.

---

