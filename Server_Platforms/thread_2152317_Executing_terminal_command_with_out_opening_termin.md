---
title: "Executing terminal command with out opening terminal"
date: 2013-06-07
forum: Server Platforms
---

### Post by dutchlab on 2013-06-07
The two severs involved are running 12.04.  I am trying to execute a shell script on a remote server without using ssh key files.  I can open a terminal on local server and run this command from the terminal ' sshpass -p 'password' ssh user@ipaddress bash /path/to/file/on/remote/server ' and the file on the remote server is executed.  However I am using Coldfusion and want to open the terminal program using cfexecute and provide this line as a parameter. The reason I am using the password method is this is a internet facing server and do not want to have the ssh key set for security reasons. 

Can someone tell me the path to the terminal executable?

---

### Post by linuxtechguy on 2013-06-07
hahahah sshkey is way more secure then a password any day of the week

---

### Post by dutchlab on 2013-06-07
unless you are on the machine the key is on then you do not need the password

---

### Post by The Cog on 2013-06-07
I would agree with lnuxtechguy although I would not be so rude about it. An ssh key setup would be more secure than using ssh passwords. The keys tend to be longer and much harder to guess than any password you are likely to set up. In addition, you can have a separate key per client that connects to the server, so you can easily disable just one client machine's access later if needed. 

If the client is compromised, then access to the server is compromised either way - the attacker can copy the key or copy the script. So I don't think there is a loss of security by using keys.

That said, the terminal executable is probably /usr/bin/gnome-terminal .

---

### Post by dutchlab on 2013-06-07
In this instance my thought is to store the user password combination in the database and then when the command from coldfusion is run as part of the application the user and password are supplied as a variable and not stored in any script.

---

### Post by dutchlab on 2013-06-07
Is there a mode for gnome-terninal that will not require opening it to execute a command.

---

### Post by The Cog on 2013-06-07
The command "man gnome-terminal" will show you all you need to know (use "q" to quit the manual page). 
gnome-terminal --command=whatever

But I probably wouldn't us gnome-terminal. Just launch the script and let it run in the background. Maybe log to a file.

---

### Post by hawkmage on 2013-06-07
A common problem with supplying passwords to commands even through variables is that anyone on the server may be able to see the password on the command using the ps command.  

With ssh key authentication the user needs access to both the public and private key on the client system to be able to authenticate to the remote system.  Other users do not by default have access to the private key so the only way someone other than the owner of the keys can get to them is if they have access to root or the ability to run commands through sudo.  If you have someone on the system with that level of access that you do not trust you have bigger issues.  Also with the use of the authorized_keys you can limit what commands the remote user can execute.

---

