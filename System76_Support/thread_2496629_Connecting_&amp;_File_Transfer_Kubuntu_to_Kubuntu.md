---
title: "Connecting &amp; File Transfer: Kubuntu to Kubuntu"
date: 2024-04-05
forum: System76 Support
---

### Post by Lappert on 2024-04-05
Been searching on Google and I see a lot of posts on how to connect Window machines, or even Windows to Ubuntu machines, but I'm looking for a K-K connection.

I have a new System76 Pangolin laptop; it came with Ubuntu, but I replaced that with Kubuntu 22.04 LTS. No major issues (yet). I have a 2TB SSD on one partition. I also have a very old (soon to be decommissioned) desktop running Kubuntu 15.10 (not a typo), and I have over 1TB of files of all sorts, which I'd like to port over to the new laptop. 

When connecting a phone or tablet, I use the USB-C, and that's OK for a limited set of files, and then transfer the files using Krusader on the desktop. Obviously using wi-fi or USB would take a VERY long time for approx. 1TB, and I'm hoping to avoid that.

So under all the dust I found an unused ethernet cable connected to my router. I haven't looked to see if I have a second ethernet port on the desktop mobo (Asus P8Z77-V Deluxe). I suspect I do, but if I remember, it uses a different driver, and I'd rather not get into all that complexity. I need a simple solution.

1. Is ethernet the best way to go?
2. Can I plug the laptop to the router - would that connect directly to the desktop, or does that need a special app or configuration?
3. Or do I need to go direct from laptop to desktop, and what would I need to do to make it work?

I realize this isn't a specific System76 question, but I thought I'd ask; apologies if the wrong forum. Any thoughts are very much appreciated.

---

### Post by TheFu on 2024-04-07
This definitely is a generic computing question. Nothing specific to System76 or Ubuntu or even Linux.  This is a very general networking and file sharing question that applies to all computing devices - android, iOS, Apple, MS-Windows, Linux, Unix, VMS, TSO, VAX, ... any computer that supports networking.

If you have 2 Ubuntu systems, the easiest way to connect between them is over what network connection already exists on the LAN that the 2 systems share.  If they both connect to the same router, then that's the network to use.

Next you get to choose which protocol you want or choose all the protocols. There are many. Each is different and "good" for specific types of use.

In general, the first sort of network connection that I setup is using ssh.  This provides ssh, scp, sftp, at the same time.  So you have a way to connect via terminal between the two systems AND 2 ways (scp/sftp) to transfer files in either direction between any systems on your LAN.  Many Linux File Managers support "sftp", just use a  URL that starts with sftp://192.xxx.xxx.xxx/   <--- point it at the IP or DNS or hostname.local of the other machine.  You'll be prompted for a password, if you didn't setup ssh-keys already (just 2 commands) and then you'll be able to browse the files/storage anywhere on the other computer.  Normal permissions apply, so most of the time, only your HOME directory on each computer will be read-write with everything else read-only.

ssh/scp/sftp are secure enough to be used over the internet too.  However, they aren't designed to be used like CIFS networked storage.  I have good news.  There are a few other protocols that ARE designed to be used as network storage.  Since you have ssh setup, you can install **sshfs** and remotely mount storage over an ssh-tunnel to your local machine using **sshfs.**  There are times when this quick method is ideal.

But there is a native, faster, more stable, server-to-server method called NFS.  NFS storage is a way to mount remote storage on different client machines.  It is high-performance and extremely stable. It has been around for 30+ yrs and "just works".  99% of programs don't know the difference between local storage and NFS remote mounted storage.  
```
$ dft
Filesystem                                       Type  Size  Used Avail Use% Mounted on
...
istar:/d/D1                                      nfs4  3.5T  3.5T   28G 100% /d/D1
istar:/d/D2                                      nfs4  3.6T  3.6T   22G 100% /d/D2
istar:/d/D3                                      nfs4  3.6T  3.6T   23G 100% /d/D3
istar:/d/D6                                      nfs4  3.6T  3.4T   68G  99% /d/D6
istar:/d/D7                                      nfs4  3.6T  1.2T  2.3T  36% /d/D7
```
I use NFS a bunch.  If I look in /d/D1, I'll see all the files and directories of the storage there and it feels like local storage on my workstation, even though it is physically installed on a computer with hostname "istar".  All Unix permissions work exactly the same whether the storage is local or NFS.  I can edit, create, delete, files there.  Other systems can access the NFS stuff too, concurrently.  Just point the file manager to the location of the NFS mounted storage and access it like it was local storage.  It won't look like anything except another directory inside the file manager or in a shell or in whatever software you run (assuming it isn't a snap package).  Snap packages include constraints that can prevent access to any storage that isn't in specific, approved-by-Canonical, locations. Nothing we can do about that, except to avoid Snaps.

ssh, scp, sftp, sshfs are all user-to-server connections.  NFS is server-to-server, so once setup ALL users on the NFS client can use the mounted storage as their Unix file permissions allow.

So, you have some choices to make.

---

### Post by TheFu on 2024-04-07
Just realized, I didn't tell you what to install.

On both systems, run these commands to install ssh.

```
sudo apt update
sudo apt install ssh fail2ban sshfs
```

There may be an addon for KDE's file manager to enable sftp:// URL support.  Let me google that:  [https://docs.kde.org/stable5/en/krusader/krusader/remote-connections.html](https://docs.kde.org/stable5/en/krusader/krusader/remote-connections.html) explains the many different protocols supported.  After running those 2 commands, you can use the sftp:// method.   

I find it interesting the nfs:// is supported, since that would be an odd way to make an NFS connection. Usually, NFS mounts are handled in the /etc/fstab file. I'd never use a file manager to mount NFS storage.  I actually doubt it would work since NFS mounts require sudo/root privileges. [https://docs.kde.org/stable5/en/krusader/krusader/mount-man.html](https://docs.kde.org/stable5/en/krusader/krusader/mount-man.html) seems to be the KDE mount manager. I'd never heard of it before, but the last time I ran a system with KDE was around 2003, so that isn't surprising.

---

### Post by Lappert on 2024-04-07
TheFU, thank you for your replies.

I've been tinkering with this the last few days and have a solution that incorporates some of your suggestions.

I took the old ethernet cable that's been sitting in the router, but no longer need for other devices, and plugged it into the laptop. I did not need to go directly from desktop to laptop.

So from the laptop I accessed the router web page (the router came from my ISP). I refreshed the page an it discovered the connection to 192.1.0.x, so that gave me the IP number. Then, from Krusader, under Tools > New Net Connection:

Under protocol I tried ftp, smb, but it was sftp that worked. (I believe I have SSH on the desktop as I use it to communicate via terminal with our off-site server but not looking for the complication)

So I selected sftp, the IP number from above, and whatever port it defaulted to (I think it was 21). I also put in the user/password for the user on the desktop (I was doing this from the laptop).

Again, using Krusader, I was able to access the directories in the desktop and in the 2nd panel, the laptop directories. And I used that to copy just as I would any other local copy situation.

I realize that if I used SSH through a terminal, I could use a variety of other commands as you explained, but this was good enough. And the speed was very good, transferring more than 1TB within 2-3 hours (with USB that could take days).

I do appreciate your extended explanation of other protocols. While I may not need it for this situation, I'll keep these in mind if and when I need more extensive capabilities.

Thank you.

---

### Post by TheFu on 2024-04-08
I didn't meantion plain FTP nor did I meantion CIFS/SMB.  There were good reasons I didn't.

Since 2002, nobody, nobody, anywhere shoujld be using plain FTP.  Period.  You can google for all the reasons why.

CIFS/SMB/Samba are protocols for MS-Windows.  You didn't mention MS-Windows, so you should use native protocols for Unix-like systems that are actually designed to work like Unix.

If you had ssh installed previously, then you would get scp, sftp too. They are included.  That's why SMB:// and FTP:// didn't work.  You should still install the other options I showed, BTW.  You can look up what they do to understand why.

Transferring with a directly connected USB3 should should be faster than connecting that same USB3 device to a different computer, then using a network transfer.  If that isn't happening, there are other issues.

BTW, sftp/scp/ssh all work on port 22, by default, but it is common to reconfigure to a different port on the ssh-server. If you didn't do that, then it wasn't done.
You can look in /etc/services for a listing of the ports used by default on your system.  

I cannot stress this enough - NOBODY should be using plain FTP anymore. NOBODY.

---

### Post by Lappert on 2024-04-09
TheFu,

Thanks for your clarification. I ended up using sftp (not ftp) and I take your concerns with all seriousness.

Both machines here use Kubuntu, not Windows.

I may eventually get to the SSH, but I was looking for a quick way of moving a lot of date from the old to a new machine.

So again, thank you. Appreciate your help.

---

### Post by TheFu on 2024-04-09
a) If this is SOLVED, please mark the thread that way, using the Thread Tools button. This helps save time for people searching for answers AND people looking to help.

b) ssh-based transfers are easy, but they are 1-user to 1-system.  NFS is system-to-system, for all users. Also, NFS is the native way that files have been shared on Unix for over 30 yrs - maybe longer.  NFS is more efficient and the setup isn't THAT hard for systems on the same LAN, provided a few caveats are understood and used.  NFS doesn't use a password for individuals either.

The only time I use sftp is when I'm away from home.  On the LAN, I use NFS or scp. My systems all have ssh, scp, sftp capabilities without a password required once I login and unlock the ssh-keys.  That could be once a day or once every few weeks, if I don't logout.  ssh-keys are shared by about 50 other ssh-based tools, including sftp.  They not only make connections and transfers more convenient, but also much more secure, since users aren't temped to insecurely save passwords all over the place in poorly create programs.

FYI, ssh is the backbone of secure Unix-to-Unix communications. There is so much that ssh can do, easily.  [https://blogs.perl.org/users/smylers/2011/08/ssh-productivity-tips.html](https://blogs.perl.org/users/smylers/2011/08/ssh-productivity-tips.html) is from 2011, so the ciphers used back then shouldn't be used anymore, but the other aspects are still 100% valid.

---

### Post by Lappert on 2024-04-09
Thank you. I marked the thread as solved.

---

