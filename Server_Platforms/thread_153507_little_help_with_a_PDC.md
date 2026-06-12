---
title: "little help with a PDC"
date: 2006-04-01
forum: Server Platforms
---

### Post by whosmatt on 2006-04-01
I'm testing a linux PDC proposal for a small company with about 15 XP workstations and about 15 mac OS X workstations.  They are complaining about poor password/authentication management on the windows side of things, and have a very limited budget.... they have a file server currently running win2k pro.  

The mac workstations are video workstations and don't have much to do with the windows side of things as far as I can tell.  They mentioned implementing a fibre channel SAN in the future for the macs, but I think they are planning on using Apple hardware and sofware for that.

I suggested to them that (since they don't want to pay for windows server) we should set up a new server running samba acting as a PDC, adding the current file server as a domain member and leaving the data on it.  the PDC will initially be used only to authenticate, and perhaps to store roaming profiles.

I've chosen ubuntu for several reasons: 

1) i'm most familiar with debian.
2) my cheap pc testbed is too "bleeding edge" in the chipset department for debian stable.  The production server, should the company choose to go with our propsed solution
3) there is an excellent how-to guide here: [http://www.howtoforge.com/samba_setup_ubuntu_5.10](http://www.howtoforge.com/samba_setup_ubuntu_5.10)

So, I installed Ubuntu on my test system, using the "server" option at the boot prompt.  

I followed the directions in the above referenced how-to to the letter, with the following exceptions:

I'm testing on my home network, and I had already configured my router (sveasoft wrt-54g) for static dhcp on my test box, so I did not hard-code the TC/IP info.

the quota install wasn't the same since I dont have a separate /home partition.  (can someone explain why installing quota is necessary?)   I can imagine why it would be advantageous with roaming profiles, but I assume it's not necessary.

I did not make entries in my /etc/hosts file for all my computers, since i have a DHCP setup and a mix of windows, mac, and linux.  Also, I have quite a few laptops that come and go.   I did, howerver, change the resolution order to add WINS to that.

Anyway, everything else was to the letter.  After I finished, I tested my server, first with XP pro running in virtual PC on my powerbook, and then with XP pro on my roomate's computer.  I made 2 accounts, and made sure that roaming profiles were working.

Then I tried to change passwords from windows.  The computers hung at the prompt.   I forcefully shut them down.  I then went on to testing roaming profiles.  those seemed to work ok, though I got errors when I tried to login as the same user on both systems simultaneously.  After that happened, I was no longer able to login to my domain as any user on either system.

Restarting samba didn't help.  restarting the entire server didn't help.  I replaced the entire smb.conf file with another one copied directly from the article (i made the first one by hand) and modified to match my domain and netbios names.  nothing doing.

so, i'm in the process now of starting from scratch.  what I want to know is: where did i go wrong?  everything seemed to work great except for changing passwords, and then of course the server broke.

Thanks for any input. 

Matt

---

### Post by LordHunter317 on 2006-04-01
Posting smb.conf would be useful.

And in reality, they should pay for a copy of Windows Server and run Active Directory.  The feature differences alone justify the cost.

---

### Post by whosmatt on 2006-04-01
here's my smb.conf

```
[global]
   workgroup = TESTDOMAIN
   netbios name = testbed
   server string = %h server (Samba, Ubuntu)

   
   passdb backend = tdbsam
   security = user
   username map = /etc/samba/smbusers
   name resolve order = wins bcast hosts
   domain logons = yes
   preferred master = yes
   wins support = yes
   
   # Set CUPS for printing
   printcap name = CUPS
   printing = CUPS
   
   # Default logon
   logon drive = H:
   ;logon script = scripts/logon.bat
   logon path = \\testbed\profile\%U


   # Useradd scripts
   add user script = /usr/sbin/useradd -m %u
   delete user script = /usr/sbin/userdel -r %u
   add group script = /usr/sbin/groupadd %g
   delete group script = /usr/sbin/groupdel %g
   add user to group script = /usr/sbin/usermod -G %g %u
   add machine script = /usr/sbin/useradd -s /bin/false/ -d /var/lib/nobody %u
   idmap uid = 15000-20000
   idmap gid = 15000-20000


   # sync smb passwords woth linux passwords
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
   passwd chat debug = yes
   unix password sync = yes
   
   # set the loglevel
   log level = 3


[homes]
   comment = Home
   valid users = %S
   read only = no
   browsable = no


[printers]
   comment = All Printers
   path = /var/spool/samba
   printable = yes
   guest ok = yes
   browsable = no


[netlogon]
   comment = Network Logon Service
   path = /home/samba/netlogon
   admin users = Administrator
   valid users = %U
   read only = no


[profile]
   comment = User profiles
   path = /home/samba/profiles
   valid users = %U
   create mode = 0600
   directory mode = 0700
   writable = yes
   browsable = no
```

---

### Post by whosmatt on 2006-04-01
Update:  

I started from scratch again, and this time working ok with no breaking (yet) but still can't change pass from windows.  Do i need to be using something besides tdbsam for this to work?

Matt

---

### Post by whosmatt on 2006-04-02
more update:

still working but changing password from windows is problematic.  when i try to change the password, i get the infamous hourglass cursor and the computer hangs for about 15 mins or 1/2 hour.  i then get a message on the windows box that the domain is not available.

the strange thing is that the password does eventually change, both on the samba side and on the unix side, it just takes a while for the change to propagate (like overnight, or perhaps after a complete restart of the server)

if i can get this working, i'm golden. having some profile quirks, but i think i can get that sorted out with some troubleshooting.

thanks for any input.

matt

---

### Post by LordMerlin on 2006-04-13
Hi whosmatt, 

I take it you have had no luck as of yet, right?

---

### Post by smeagol on 2006-04-13
I've seen authentication issues in a Windows only environment, as well as slow logons, and while I have no exact fix for you to try, I think running ethereal on the network might provide some insight.  See what kind of traffic you are getting from the client machine during the password change attempt process.  Determine if the Ubuntu PDC is receiving this traffic and what's going on after that.  If you see lots of broadcasts, it could just be inefficient network traffic causing the slow password changes. Is NetBIOS over TCP/IP disabled on the client? WINS entries? Maybe even add the PDC to the HOSTS file...?  I could be way off, but I figured I'd throw some ideas out there. If I *am* onto something, here's a link with info on Windows name resolution: [http://www.comptechdoc.org/os/windows/wintcp/wtcpname.html](http://www.comptechdoc.org/os/windows/wintcp/wtcpname.html)


I was reading that same howtoforge article, and I was going to actually try it on my home VMWare test box as well. If I get to it soon, I'll post my results.

Good luck.
Brian

---

### Post by linuxmad on 2006-05-01
Hi,
Don't know if I can help...:confused: , but i have followed the same tuto and ...yes i had the same problem, so i just did this:
 ```
unix password sync = Yes 
```
to 
```
unix password sync = no
```

And I am able to change passwords:p 

Please let me know if it worked...

---

