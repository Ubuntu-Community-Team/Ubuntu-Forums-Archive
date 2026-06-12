---
title: "FTP Users problem"
date: 2013-05-25
forum: Server Platforms
---

### Post by Di0g0 on 2013-05-25
Hi

I have the following problem:

I have a gaming panel running on my VPS, but that panel only allows users to start and stop the server, so I need to create an ftp account in my VPS to allow them upload the game files.

The problem there is, my gaming panel uses an SSH connection to start&stop servers so i can't block shell to the user used by the panel. I want to create other accounts and block the accounts to a folder on other ubuntu account.


Example:

Game Panel --> Connects using linux account: servers (Via SSH) /home/servers/

Now I will create 2 folders inside of this home/servers/, 1 folder named SAMP, and another named Minecraft.

Now I need to create 2 FTP users blocked to /home/servers/SAMP/ and another blocked to /home/servers/Minecraft with full acess to this folders (Write,Read,Execute), but without shell acess.

Thanks

---

### Post by Lars Noodén on 2013-05-26
Since you already have SSH running one way to go about allowing uploads would be to use SFTP.  That's built into your SSH server.  

Also, with SFTP it is easy to lock down and disallow shell access for groups of users.  Use a [Match](http://manpages.ubuntu.com/manpages/raring/en/man5/sshd_config.5.html) directive in sshd_config.

```

Subsystem sftp internal-sftp

Match Group sftp-only
        AllowTCPForwarding no
        X11Forwarding no
        ForceCommand internal-sftp

```

Then to allow SFTP access, but disallow shell access, just add the users to the grouo *sftp-only*.

If you want something more complex with virtual users that exist only in the (S)FTP server, then there is VSFTPd.

---

### Post by Di0g0 on 2013-05-26
Ya, but that only prevents shell access.. or I'm wrong? I can lock a user to other user folder ?  If the answers is yes, where I have to config the path for that user? Each user have a different path 

Like this:

user servers contains all the servers inside his home directory.

paneluser only can view via sftp the folder /home/servers/paneluser.

---

### Post by Lars Noodén on 2013-05-26
You can also lock a user to a specific folder using the [ChrootDirectory](http://manpages.ubuntu.com/manpages/raring/en/man5/sshd_config.5.html) directive.  The tricky part with that is that the chroot destination must be owned by root and not writeable by anyone else.  However, subdirectories can be owned and writable by whoever.  

So if you chroot to * /home/servers/* you can have * /home/servers/paneluser* owned and writable by your user.  Then you could connect directly to that directory:

```

sftp user@server:/paneluser

```

Note that there the directory will appear to be in the root directory because of the chroot.

---

### Post by Di0g0 on 2013-05-26
I'm a bit confused... Can you make an easy tutorial with the basic steps so I can try?

I formatted my VPS because I messed up my ubuntu :(

---

### Post by Lars Noodén on 2013-05-26
Well, before starting you'll need to search around for material about chroot so that you know what it does.  In a nutshell, it makes a subdirectory appear to be the root directory for a user or process and nothing above that directory should be visible.

Next you'll have to work with the ssh server's configuration file, sshd_config.   The changes you need to make are very simple so there will not be much written about them, it's mostly a matter of getting comfortable with what the [manual pages for sshd_config](http://manpages.ubuntu.com/manpages/raring/en/man5/sshd_config.5.html) say about the directives you will use.

```

Subsystem sftp internal-sftp

Match Group sftp-only
        AllowTCPForwarding no
        X11Forwarding no
        ForceCommand internal-sftp
        ChrootDirectory  /home/servers/

```

Look up Match, ForceCommand, and ChrootDirectory in the manual page for sshd_config(5).  The above will allow any user in the group sftp-only to connect with SFTP but otherwise not be able to log in.  Further, it will restrict those users to what is within the directory  */home/servers/*, which could mean the directory *paneluser*.

---

### Post by Di0g0 on 2013-05-26
Thanks!

Then it is possible to give account servers permissions to all the folders inside his home directory /home/servers/, and give permissions to the user paneluser only on his folder /home/servers/paneluser?

---

### Post by Lars Noodén on 2013-05-26
Yes, but the [permissions](https://help.ubuntu.com/community/FilePermissions) would be handled the same as regular file and directory permissions in Linux.  It's not something peculiar to ssh.  

In general if you want group write access, you have to assign permissions on a group basis and have the accounts be members of that group to be affected.

---

### Post by Di0g0 on 2013-05-26
Thanks

How can I limit a specific user to can only acess via SSH/SFTP from only 1 IP defined by me?

Nvm, i solved that alone. Thanks anyway!!

---

### Post by Lars Noodén on 2013-05-26
I'm guessing that it would be something like this in [sshd_config](http://manpages.ubuntu.com/manpages/raring/en/man5/sshd_config.5.html).  You'd need to have Match conditional blocks for both conditions.

```

Subsystem sftp internal-sftp

Match Group sftp-only, Address 192.168.0.100
        AllowTCPForwarding no
        X11Forwarding no
        ForceCommand internal-sftp
        ChrootDirectory  /home/servers/

Match Group sftp-only, Address *,!192.168.0.100
        DenyGroups sftp-only

```

Mind the spaces, or lack of them.

---

### Post by Di0g0 on 2013-05-26
I can't make this this way...

Can you explain me how I can chroot ssh users to his home directory? And allow sftp chrooted to their home folder.

And if I make this, they can execute scripts and servers?

---

### Post by Lars Noodén on 2013-05-26
There is one trouble with chrooting users to their home directories, the chroot target has to be owned by root and not writable by anyone else.  So if you have fairly static content in the home directories, you can do that and still leave all the files and subdirectories under the ownership of the user.  Otherwise, if you can't chown the home directories you can still point them to /home instead.

So if you can chown the home directory to root, then you could do it like this:

```

Subsystem sftp internal-sftp

Match Group users
        ChrootDirectory %h
        AllowTCPForwarding no
        X11Forwarding no
        ForceCommand internal-sftp
```

%h gets substituted with the actual home directory of the user logging in.

Otherwise, you can point them to /home and them have them cd to their directory.

```
Subsystem sftp internal-sftp

Match Group users
        ChrootDirectory /home
        AllowTCPForwarding no
        X11Forwarding no
        ForceCommand internal-sftp

```

---

### Post by Di0g0 on 2013-05-26
Ok, but how i can allow ssh connection?

And if they are chroot they can acess the linux system folders and things like that to execute the game server on that account?

---

### Post by Lars Noodén on 2013-05-26
The interactive SSH connection is harder to chroot, even if SFTP is easy.  If you want to allow interactive login to a chrooted directory, you need to include at least a shell (e.g. bash) and basic /dev nodes such as null(4), zero(4), stdin(4), stdout(4), stderr(4), arandom(4) and tty(4) devices. It requires a bit of setting up, then they can only access the files and programs within the chroot.  What are you trying to arrange?

---

### Post by Di0g0 on 2013-05-26
I have a VPS when I need to create 2 users, one for minecraft other for SAMP. (2 different games)

Each account will have a folder with the game files inside.

Now the Minecraft guy needs to acess via FTP the account minecraft to update files and needs SSH to execute the scripts in order to start the server.
The same for SAMP guy.

But I want to block acess outside each ubuntu account (Minecraft/SAMP). Only give access to his home folder.

I'm working on this 3 days and I can't solve the situation :s

---

### Post by Di0g0 on 2013-05-26
If i block SSH to an ip SFTP will be blocked to that ip too?

---

### Post by Lars Noodén on 2013-05-26
I was at first thinking changing their shells to [/bin/rbash](http://manpages.ubuntu.com/manpages/raring/en/man1/rbash.1.html) and doing some tricks with the $PATH but after doing a little experimenting, it might be doable with restricted keys.  They need to run SFTP and one script, right?  

If that is the case, you can make two keys for each user, one to run SFTP one to run a script.  If you have several scripts, you need one key per script.  Make two or more keys (using strong passphrases) for each user, then make sure they can log in with those keys.  Once that is in place, log into the server and edit their ~/.ssh/authorized_keys files on the server and prepend forced commands to each key.  One command will be for the script the other will be to force sftp.

```

command="/usr/local/bin/somescript"  ssh-rsa AAAAB3NzaC1yc2EAAAA....
command="/usr/lib/openssh/sftp-server" ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCi+k1d0agqW...

```

Then on the client workstation the script can be launched like this:

```

ssh -i ~/.ssh/script_rsa_key *user@server.example.org*

```

And sftp launched like this (of several ways).

```

sftp -i ~/.ssh/sftp_rsa_key *user@server.example.org*

```

---

### Post by Lars Noodén on 2013-05-26
> **Di0g0 said:**
> If i block SSH to an ip SFTP will be blocked to that ip too?

If you block SSH with iptables (firewall) then SFTP will be blocked, too.  If you want only SFTP but not SSH , see the trick above.

---

### Post by Di0g0 on 2013-05-26
Here the client put this? Putty? [COLOR=#000000][FONT=Ubuntu Mono]ssh -i ~/.ssh/script_rsa_key [/FONT][/COLOR][I]user@server.example.org
[/I]
Ya they only need to run a file to start the server ahhh an another to stop the serve, in the SAMP case the only way to stop the server is killing the PID :s

---

### Post by Lars Noodén on 2013-05-26
> **Di0g0 said:**
> Here the client put this? Putty? [COLOR=#000000][FONT=Ubuntu Mono]ssh -i ~/.ssh/script_rsa_key [/FONT][/COLOR]*user@server.example.org*

PuTTY should do everything you need as far as connecting goes, but I haven't used it on Linux.  Is there an Ubuntu version?

I would try to set everything up from Linux first and then load the keys into PuTTY.  Here's one tutorial how:

[http://www.howtoforge.com/ssh_key_based_logins_putty](http://www.howtoforge.com/ssh_key_based_logins_putty)

But it will only work after you have the keys ready.

---

### Post by Di0g0 on 2013-05-26
> **Lars Noodén said:**
> If you block SSH with iptables (firewall) then SFTP will be blocked, too.  If you want only SFTP but not SSH , see the trick above.

My new idea was installing a control panel on a web host to start & stop the servers. The panel will use a ubuntu account to SSH to the VPS.

After that I will create 2 folders inside that account homefolder one for each server, and arrange a way to give them FTP access to change the files.

---

### Post by Lars Noodén on 2013-05-26
> **Di0g0 said:**
> My new idea was installing a control panel on a web host to start & stop the servers. The panel will use a ubuntu account to SSH to the VPS.

After that I will create 2 folders inside that account homefolder one for each server, and arrange a way to give them FTP access to change the files.

You could have a shell script with a short menu of actions to start the servers and such and tie the ssh key (the one on the server in ~/.ssh/authorized_keys) to that script.  It's sounding more like keys might be the way to go.  One key to start/stop/reload the server another key for SFTP.  Making a web UI would add a lot of complexity.

---

### Post by Di0g0 on 2013-05-26
> **Lars Noodén said:**
> You could have a shell script with a short menu of actions to start the servers and such and tie the ssh key (the one on the server in ~/.ssh/authorized_keys) to that script.  It's sounding more like keys might be the way to go.  One key to start/stop/reload the server another key for SFTP.  Making a web UI would add a lot of complexity.

But in the SAMP case, the only way to stop that kind of servers is killing their PID. Is there anyway to create a key to stop samp servers killing a random PID? :(

Also

About my new ideia, I have a web panel that connects via SSH to the machine to start & stop servers, the problem is that the panel doesn't have any web ftp option so I need a way to upload files to FTP to a specific folder.

---

### Post by Lars Noodén on 2013-05-26
In the SAMP case, is the PID saved in a file?  Often servers will store their PID in a special log file which can then be used to kill the file.

```

kill -HUP $(cat /var/run/samp.pid)

```

Or else maybe [pkill](http://manpages.ubuntu.com/manpages/raring/en/man1/pkill.1.html) can be used to kill it by name.  If you have the exact name of the program, it should work like this:

```

pkill -HUP -x sampd

```

Where instead of 'sampd' you would write the name of the SAMP server program.

---

