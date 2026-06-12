---
title: "setting up keys for ssh for multiple users"
date: 2011-01-30
forum: Security
---

### Post by F35 on 2011-01-30
Ubuntu 10.10 Server is loaded.  Openssh has been loaded. 

I have multiple users which need access to server via ssh.

My impression from reading about ssh is that a key needs generated for each person.  Thus, each key will have a passphrase that is unique to them. 

In /etc/ssh/sshd_config, the default sshd_config suggest using:

%h/.ssh/authorized_keys
My assumption is %h is a variable that will allow the current user to use the public key stored in his home directory under the .ssh folder in a file called authorized_keys.  Is their a command string that automatically populates the authorized_keys file?

Please let me know if I have misunderstood something above. 

I am surprised that even though there are a number of hidden (e.g. .****) files located in the home folder, there is not one automatically generated as .ssh.  It appears I have to create that directory myself.  I am especially surprised by this since it appears the instructions for generating a key seems to load the key in the home directory instead of proceeding to create a .ssh folder to store the keys in. 

It is not clear, but it appears that the public key needs to be copied or appended to the authorized_keys file, but, using the scheme above, the public key needs to be copied or appended to each users authorized_keys file instead of appending all public keys to a single authorized_keys location. 

It then appears that each persons authorized_keys file needs permissions set to 600.

It also appears that if I decide to use RSA instead of DSA, I would do the same thing above but would use authorized_keys2 file instead.

Again, please let me know if I have misunderstood something. 

Why doesn't the home folder which gets automatically set up for each user automatically get a .ssh folder generated?  i.e Why does it have to be created by hand?  Does it need the same permission on the .ssh folder?  ie  600?

My aim is to allow many to log on via ssh simultaneously and then allow many to simultaneously vnc into their respective gnome desktops.

Is what I have above going to get me going in the right direction?

---

### Post by HermanAB on 2011-01-30
Yep that looks right.  Ubuntu doesn't configure SSH by default.  If you want a more user network security oriented system, use Fedora or OpenSuse.

The only issue I see is that running VNC over SSH is redundant.  Once SSH is working, you don't really need VNC anymore.  VNC is mainly a Windows thing and a better solution is plain vanilla SSH or nomachine.

For example, you could run a Gnome panel remotely.  Anything you then launch from that panel, will also run remotely and will open transparently on the local desktop:
$ ssh -X -C -c blowfish user@server gnome-panel

Nomachine does the same thing, but it adds some more compression than the SSH -C parameter, so it is a little faster, at the expense of being more troublesome to get to work than plain vanilla SSH.

---

### Post by F35 on 2011-01-31
I am using putty to connect.  I ran the command you suggested, except I had to declare a different ssh port than 22 but got the following:

Write failed: Broken pipe

then, upon trying again got 

Permission denied (publickey)

So, yes, I am very interested in running without VNC but have never done so.  It looks like the ssh command you offered will spawn a new desktop session for each user.

Let me clarify my confusion.  I was able to connect to ssh and get into a remote terminal session like normal.  Then when I issued the command above it said permission denied.  I don't understand how I could acquire access into openssh using the publickey but then not be able to run gnome based on the same publickey I had just used.

---

### Post by F35 on 2011-02-05
I continue to be stuck.  I would love to see this work:

        user@server:~$ ssh -p 2233 -X -C -c blowfish user@server gnome-panel


However, I continue to get this:

        Permission denied (publickey)

I am ssh'ing from putty to get to the terminal.

---

### Post by cariboo on 2011-02-05
Putty uses a different key format from ssh. Have a look [here]("http://linux-sxs.org/networking/openssh.putty.html") for a putty/openssh howto.

---

### Post by F35 on 2011-02-05
Thanks for the correspondence!  However, I have looked there.  

The only instructions I have found suggest a command similar to this:

ssh -p 2233 -X -C -c blowfish user@server gnome-panel

Here is what is confusing: In order for me to issue this command, it appears that I have to first connect into the ssh host via putty.  I then get a terminal screen back on my client (windows machine) where I can log in.  Once logged in (with my ssh keys), I am logged in to the host.  My ssh keys have already been used.  They have passed the test.  Then, at the prompt on the terminal screen, I then type 

ssh -p 2233 -X -C -c blowfish user@server gnome-panel

That is when I get the 

Permission denied (publickey)

Why am I confused?  Well, because I have already used my key successfully to get onto the host.  I know the key is ok.  So, why would the key be denied.

My impression is that HermanAB, in his post above, was giving me the command that works for him when his client is linux and his host is linux.  So, maybe he is issuing the 

ssh -p 2233 -X -C -c blowfish user@server gnome-panel

command from his client.  Of course this is not what I am doing....I am issuing that command on the host.  I don't see a way to issue this command from Putty from my windows client.  

So, if I happen to be right about the advice that HermanAB gave me, then what I really need is a command that I can issue on the host while no one is actually logged into the machine.  

Any one think that my guess is correct about what HermanAB intended?

Any one got a command I can issue on the host (remotely from the client via putty) which will spawn a virtual gnome session (preferably using only ssh as HermanAB suggested (not having to use vnc))?

---

### Post by cariboo on 2011-02-06
HermanAB's command is only useful if you are running a Linux variant, it won't work if you are running putty+Windows.

Have you had a look at [nomachine]("http://www.nomachine.com/")?

---

