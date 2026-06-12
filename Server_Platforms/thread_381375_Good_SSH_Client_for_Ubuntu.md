---
title: "Good SSH Client for Ubuntu ?"
date: 2007-03-10
forum: Server Platforms
---

### Post by kevmartin on 2007-03-10
Hi,

I'm in the process of switching from windows to ubuntu, and bit by bit finding replacements for functionality I had in Windows.  But I'm stuck on one here and thought users of this forum might have a suggestion.

I need a good SSH client that will remember passwords.  I log in regularly to a large number of servers regularly by SSH, and it is really a pain to have to manually look up and type in passwords every time.  Putty doesn't even allow cut and paste, so I really do have to type them in, which is tedious with random character passwords in particular, such as 5djD6%hSj$g (even more so for those of us not blessed with touch typing skills).

Is there a way? Or am I going to have to fire up virtualbox and windows to use my old Windows GUI app for this (that prospect does not excite me lol)

Thanks

---

### Post by gborzi on 2007-03-10
AFAIK, there isn't an ssh clients that remembers the passwords. However, there is a way to avoid remembering all the passwords:
[LIST=1]
[*]Generate a pair of authentication keys with *ssh-keygen -t rsa* on your computer (I'll call it A). Enter a password for the generated keys when requested.
[*]Login to the remote computer (I'll call it B), create a .ssh directory in the home *mkdir ~/.ssh* if it isn't already there.
[*]Append your public ssh key on computer A to the file ~/.ssh/authorized_keys on compter B, i.e. *cat ~/.ssh/id_rsa.pub | ssh <your B login>@B 'cat >> .ssh/authorized_keys'*
[*]Now, when you ssh to B the system it will ask for the password you gave in 1.
[/LIST]
In this way you have to remember only one password, that of your ssh key couple. If you don't want to remember even this single password, enter a blank password in 1. Or you can use ssh-add to enter the password only once per X session.

---

### Post by Mr. C. on 2007-03-10
The fucntionality you need is enabled by the ssh-agent, which is already running when you login to the GDM X11 environment.  The previous poster indicated how to add keys.

For more info, review:

man ssh-agent

MrC

---

### Post by kevmartin on 2007-03-11
Thanks for the input guys.  It didn't really work for me.  I created the key OK, but it's extremely hampered by Putty not allowing cut and paste.  My key had around half a dozen characters in it that could have been either one's or small L's (the two seem to look identical in Putty so theres no way to tell).  So I'm guessing I got one or more of them wrong - but the number of combinations to try by trial and error would be huge, all of which have to be manually typed, really slowly.

Then there's the fact that some clients might not want me leaving a key on their system (I work for a host and some of our servers are dedicated).  So ...  I dunno.  May be the virtual box and my good old Windows Absolute Telnet client may be the way forward.

What amazes me is there isn't an offering in this area, even if it was commercial (likewise I haven't yet seen a Password Manager to rival Roboform).  I thought linux was supposed to be super-secure, so why not I figure?

---

### Post by Rizado on 2007-03-11
You shouldn't use putty in linux. The openssh client is much better and to save passwords use ssh-agent.

If you want to create authentication keys here's how to do it: [http://www.ubuntuforums.org/showthread.php?t=137746](http://www.ubuntuforums.org/showthread.php?t=137746) Keep in mind that everyone who need access need the private key. Might be a bit of a hassle but it's very secure. That is if you disable regular passoword authentication.

BTW: Isn't rsa less secure than dsa?

---

### Post by kevmartin on 2007-03-11
Thanks - I'm more than willing to try openssh ... but ...

My system shows openssh is installed in synaptic, but I can't find a way to start it, or add it to start menus.  It's not in usr/bin to start manually from there, and running "openssh" in command line gives "command not found".  Seems I'm doing something wrong.

Thanks again

---

### Post by Rizado on 2007-03-11
> **kevmartin said:**
> Thanks - I'm more than willing to try openssh ... but ...

My system shows openssh is installed in synaptic, but I can't find a way to start it, or add it to start menus.  It's not in usr/bin to start manually from there, and running "openssh" in command line gives "command not found".  Seems I'm doing something wrong.

Thanks againOh sorry, the ssh command is called ssh: ```
ssh user@theip
``` Enter and done! You'll now be able to copy and paste and do whatever you want :) (Even start X applications from the other computer if they have it enabled.)

---

### Post by tribaal on 2007-03-11
You just type "ssh <username>@<host>" at the prompt.
You shouldn't need to have something that remembers your passwords. Just create yourself an ssh key, and copy it to ~/.ssh/authorized_keys2 on every machine you want to access.

Ps: SSH is native to linux ;) No need for putty or anything like that :)

- trib'

---

### Post by Rizado on 2007-03-11
> **tribaal said:**
> You just type "ssh <username>@<host>" at the prompt.
You shouldn't need to have something that remembers your passwords. Just create yourself an ssh key, and copy it to ~/.ssh/authorized_keys2 on every machine you want to access.

Ps: SSH is native to linux ;) No need for putty or anything like that :)

- trib'I'm pretty sure it's only authorized_keys in newer openssh. This is adjustable in /etc/ssh/sshd_config.

---

### Post by kevmartin on 2007-03-11
That's much better thanks :-)

I always did hate Putty the couple of times I tried it on Windows (Absolute Telnet was infinitely better), but now I don't need to worry about it.  I can live with copy/pasting IP and password until I get keys organized on all the servers.

Thanks again.

---

### Post by tturrisi on 2007-03-11
fyi, it want to use a gui ssh, gftp handles it well.

---

### Post by Mr. C. on 2007-03-11
> **kevmartin said:**
> That's much better thanks :-)

I always did hate Putty the couple of times I tried it on Windows (Absolute Telnet was infinitely better), but now I don't need to worry about it.  I can live with copy/pasting IP and password until I get keys organized on all the servers.

And in case someday you need a better SSH client in Windows :

Free: Tunnelier
$$$: securecrt

MrC

---

### Post by kevmartin on 2007-03-11
> **tturrisi said:**
> fyi, it want to use a gui ssh, gftp handles it well.

I see that yes - good for file transfers, but no command line that way.  I am also looking at options for a FTP program though, so will be trying it out.  In Windows I used WS_FTP Pro which I was very impressed with after never being quite satisfied with other clients (I really love the tabbed interface of WS_FTP for multiple connections in one window).  I found a Firefox extension called FireFTP which seems pretty good too.

Thanks

---

### Post by tturrisi on 2007-03-12
On my windows boxes I use WinSCP because it's:
1. free
2. very stable
3. works well
4. can use a commander style interface (2 pane drag+drop)

for plain ftp I still just use FTPXplorer (for last 9 yrs)

---

### Post by tribaal on 2007-03-12
> I'm pretty sure it's only authorized_keys in newer openssh. This is adjustable in /etc/ssh/sshd_config.

Thanks for pointing this out :)

- trib'

---

### Post by TomFumb on 2007-03-17
I'm pretty sure that putty does support copying and pasting - you just have to highlight the text you want and then middle-click inside the putty window, and the text will be appended to the command line. 

However, clearly you want to use the command line in a terminal instead

---

