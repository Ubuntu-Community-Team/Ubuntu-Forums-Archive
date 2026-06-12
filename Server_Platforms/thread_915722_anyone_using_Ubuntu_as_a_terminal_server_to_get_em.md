---
title: "anyone using Ubuntu as a terminal server to get email remotely?"
date: 2008-09-10
forum: Server Platforms
---

### Post by beaker15 on 2008-09-10
Hi

i'm looking for the best way to check my email remotely from the Ubuntu server in my workplace. Its a Gutsy server with postfix on it which currently retreives mail (via fetchmail) from our ISP mailboxes. The workstations (which are WinXP) retreive mail from postfix into thunderbird profiles, also stored on the server. 

I've tried several things including the ideal solution which was to create a Putty tunnel on my home PC and just point my Thunderbird to the profile share on the server which worked but was incredibly slow, really unworkable. 

The option i'm considering is setting up a new server (we have a spare)as an Ubuntu terminal server but i have some questions.....

1. Can Windows clients connect to a linux terminal server?
2. If the tunnel needs to be SSH, will it be really slow again?
3. Is this a good solution? or could you advise on a better one





All the clients are XP and, in terms of getting remote email, need to be quite user friendly 


thanks for reading!  :)

---

### Post by cdenley on 2008-09-10
> **beaker15 said:**
> Hi

i'm looking for the best way to check my email remotely from the Ubuntu server in my workplace. Its a Gutsy server with postfix on it which currently retreives mail (via fetchmail) from our ISP mailboxes. The workstations (which are WinXP) retreive mail from postfix into thunderbird profiles, also stored on the server. 

I've tried several things including the ideal solution which was to create a Putty tunnel on my home PC and just point my Thunderbird to the profile share on the server which worked but was incredibly slow, really unworkable. 

The option i'm considering is setting up a new server (we have a spare)as an Ubuntu terminal server but i have some questions.....

1. Can Windows clients connect to a linux terminal server?
2. If the tunnel needs to be SSH, will it be really slow again?
3. Is this a good solution? or could you advise on a better one





All the clients are XP and, in terms of getting remote email, need to be quite user friendly 


thanks for reading!  :)

What do you mean by "terminal server"? Why not configure your e-mail server with SSL encryption and forget about SSH?

---

### Post by beaker15 on 2008-09-10
a terminal server would be where users connect to it remotely and work in a session on the terminal server, ie the only thing the client computer is processing is keystrokes and mouse movement. all programs, the user profile and all processing is done on the server. We use a Windows one on a different network and it works great for remote users (sorry Linux fans but it does!.

Can you explain a bit more about what you're suggesting please? Do you mean use a web browser interface to check mail, like Microsoft Outlook Web Access?

---

### Post by cdenley on 2008-09-10
> **beaker15 said:**
> a terminal server would be where users connect to it remotely and work in a session on the terminal server, ie the only thing the client computer is processing is keystrokes and mouse movement. all programs, the user profile and all processing is done on the server. We use a Windows one on a different network and it works great for remote users (sorry Linux fans but it does!.

Can you explain a bit more about what you're suggesting please? Do you mean use a web browser interface to check mail, like Microsoft Outlook Web Access?

I figured you were a microsoft person. The word "terminal" means somewhere where you see a command shell, except on a microsoft server. 

You have a few options for a solution like that:
-XDMCP
[http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=12&Itemid=27](http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=12&Itemid=27)
-FreeNX
[http://freenx.berlios.de/](http://freenx.berlios.de/)
-VNC

I believe all support a windows client.

I was referring to setting up whatever kind of e-mail server you want. You can use webmail, IMAP, or POP3. I believe they all support SSL encryption. You said your clients were already using thunderbird. Why not allow thunderbird to connect directly using the same method, except with SSL encryption?

---

### Post by beaker15 on 2008-09-10
thanks for the links and yeh, i mostly work on a Windows network but we also have a small network with a linux server that i'm still getting to grips with.

So, just to clarify, are you suggesting putting the public IP address of my email server into thunderbird on the home PC and set it to use SSL and set up SSL on my postfix server? no VPN or putty tunnel? sounds too easy!

---

### Post by cdenley on 2008-09-10
> **beaker15 said:**
> thanks for the links and yeh, i mostly work on a Windows network but we also have a small network with a linux server that i'm still getting to grips with.

So, just to clarify, are you suggesting putting the public IP address of my email server into thunderbird on the home PC and set it to use SSL and set up SSL on my postfix server? no VPN or putty tunnel? sounds too easy!

Yes, that is what I'm suggesting. Secure and simple.

---

### Post by beaker15 on 2008-09-10
Thanks for all the help, just one last thing:

ok, I currently have one Ubuntu server on the network acting as File&Print server, email server and everything else. As i mentioned, i do have another server not being used so my plan now is to get another IP address from my ISP and set it up as an email server in a DMZ. Question is do i need to migrate the postfix data over to the new server or is it possilble to just install postfix on the new server and somehow point it to the Main server? 

i realise i'm straying away from my original question here so apologies for that.

thanks again

---

### Post by timcredible on 2008-09-10
> **beaker15 said:**
> a terminal server would be where users connect to it remotely and work in a session on the terminal server, ie the only thing the client computer is processing is keystrokes and mouse movement. all programs, the user profile and all processing is done on the server. 

yeah, you can do the same thing in linux.  whereas windows has rdp (terminal services), linux/unix has xdm.  click on my sig on a how-to to use that, including a windows client.  you can also use vnc, but that's not native, so i always recommend xdm first.

---

