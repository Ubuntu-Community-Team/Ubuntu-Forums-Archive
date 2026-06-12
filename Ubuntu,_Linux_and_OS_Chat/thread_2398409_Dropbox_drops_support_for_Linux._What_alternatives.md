---
title: "Dropbox drops support for Linux. What alternatives do we have?"
date: 2018-08-11
forum: Ubuntu, Linux and OS Chat
---

### Post by Paddy Landau on 2018-08-11
Dropbox will [drop support for Linux]("https://www.dropboxforum.com/t5/Syncing-and-uploads/Dropbox-client-warns-me-that-it-ll-stop-syncing-in-Nov-why/td-p/290058") from November.

Well, officially, Dropbox will continue to work on Linux.

But.

Your files must be held on an *unencrypted* [FONT=lucida console]ext4[/FONT]. No other file system will be accepted.

So, [FONT=lucida console]ext4[/FONT] running on [FONT=lucida console]ecryptfs[/FONT], [FONT=lucida console]fscrypt[/FONT] or LUKS won't count! Given the EU's GDPR and other reasons, this essentially means that Dropbox has given up on Linux.

Even files on a shared NTFS file system will be supported when booting from Windows, but unsupported when booting from Linux.

I mean… like… what?!

Quite a number of people are saying that they have no choice but to cancel their contracts with Dropbox. I get the feeling that Dropbox doesn't care; the amount of money involved is too small for the company.

I was wondering what good alternatives we have to Dropbox? I use Android, so it would have to support Android. Maybe something that links with Google Drive?

Dropbox supporters have only 2½ months to replace their Dropbox systems.

---

### Post by wildmanne39 on 2018-08-11
*Thread moved to **Ubuntu, Linux and OS Chat for a more appropriate fit**.*

---

### Post by fyfe54 on 2018-08-11
[https://mega.nz/](https://mega.nz/) ?  
First 50Gigs free.  End-to-end encryption, open source code. And they don't have the keys.
Has been uneventful.

---

### Post by Paddy Landau on 2018-08-11
> **fyfe54 said:**
> [https://mega.nz/](https://mega.nz/)
Thanks. I've tried it out, and it syncs quickly and automatically from my computer to the cloud and vice-versa.

But I can't figure out how to get it to automatically sync with the Android device. Do you know how to do it?

---

### Post by TheFu on 2018-08-12
nextcloud - only use it over a VPN. Works with desktops and android.
Seafile - same as nextcloud, use a VPN.

F/LOSS clients exist. $0.  Use the source Luke. Shouldn't be any ads either.  F-Droid app-store has the GNU clients.

For many people, straight sftp is fine.  There are clients for every OS that has networking.

"Live by the cloud, die by the cloud."

---

### Post by Paddy Landau on 2018-08-12
Thanks, @TheFu. VPN is problematic for me; I often have hassles with it. Also, I don't use it on my mobile device unless I connect to other people's WiFi because it eats too much battery charge.

So, I'll skip the VPN versions. I'll try the others mentioned. SFTP would be a great idea if I had an encrypted server and the knowledge of how to implement it! Although I could use my home computer as the server, it's not always on.

---

### Post by TheFu on 2018-08-12
```
sudo apt install openssh-server fail2ban
```

Open a port on your router/firewall, perhaps 64022 and forward it to the "server" port 22/tcp.

IMHO, this is the first step anyone with a broadband connection from home should do.

Any other security things you do to lock down ssh apply automatically to sftp, scp, rsync, rdiff-backup, sshfs, and any other ssh-based tools. For example, prevent all remote root and never allow passwords to be used over the internet. Only ssh-keys or ssh-certs should be allowed. There are settings in the sshd_config file for these things. There are lots of how-to guides for securing ssh.  Heck, I wrote one too. Google finds them.

Be happy. Profit!

This "server" could easily be a raspberry pi that you leave on 24/7.  Might cost $5/yr in electricity.  I spend about $100 extra a year to power my systems. Have about 10 physical and 20-30 virtual machines.  I could use a $5/month VPS at some cloud provider as a gateway, but putting 20+ systems into the cloud wouldn't be cheaper.  A raspberry pi can easily run nextcloud and provide access internally and externally, if you like.

You can use ssh as a VPN. Look up SOCKS proxy with ssh. I haven't found openvpn sucking too much battery on my android devices. Perhaps there are other issues with yours?   I don't trust HTTPS, there are many design flaws to the entire system, so for network encryption I don't want to trust 2 3rd parties (DNS and certificate authorities), which have been hacked or taken over by "bad guys" multiple times around the world.  Using certs that I control both on the server and client side means I don't have to trust that someone else wasn't stupid. ssh, openvpn, libreSwan VPNs let me do that on servers that I control. 

That is why I say you need a VPN to use nextcloud or seafile. I don't trust HTTPS, especially with access to my data.  Lots of people do.

---

### Post by fyfe54 on 2018-08-12
Sync with android not reallly an issue as space is limited on my android phone.  I'm at almost my 50gig limit, so I would have to sync selectively. Mega's android app however makes my files available - I can see and download them, but they do not sync

---

### Post by Tadaen_Sylvermane on 2018-08-12
I bought a license for insync google drive client. Love it. Worth the 1 time cost.

---

### Post by Frogs Hair on 2018-08-12
Just deleted my dropbox account, not much stored there to begin with. One less account to deal with.

---

### Post by TheFu on 2018-08-13
> **fyfe54 said:**
> Sync with android not reallly an issue as space is limited on my android phone.  I'm at almost my 50gig limit, so I would have to sync selectively. Mega's android app however makes my files available - I can see and download them, but they do not sync

This is Paddy's thread, but nextcloud allows you to control which files/directories are sync'd on each device.  The amount of storage available is unlimited, since you host it. 50G, 500G, 5TB, 50TB .. how much storage is completely up to you.

If you use a VPN for access when remote, then what is hosted is generally secure.  And it effectively prevents anyone in the world from even attempting brute force password access to the login page.

---

### Post by Paddy Landau on 2018-08-13
Thank you for all the comments and ideas.

I've found that [pCloud]("https://my.pcloud.com/") suits my purposes best; it seems to do everything that Dropbox does, except that it supports Linux fully.

The one downside is that pCloud doesn't have a PPA.

---

### Post by Frogs Hair on 2018-08-13
> **Paddy Landau said:**
> Thank you for all the comments and ideas.

I've found that [pCloud]("https://my.pcloud.com/") suits my purposes best; it seems to do everything that Dropbox does, except that it supports Linux fully.

The one downside is that pCloud doesn't have a PPA.

Looks like a good alternative.

---

### Post by Geoffrey_Arndt on 2018-08-14
So, just to be clear, I run Ubuntu 16.04 on a 120GiB SSD using the ext4 file system.   About two-thirds of my files are not sensitive (and are not ecrypted).    The other third are (or are border-line).    For those I prep them for Dropbox via encrypting using 7z AES encryption (which is very fast and can handle full directories as well as individual files).

Is Dropbox saying those files encrypted with 7zip compression (AES) will not be accepted for storage . . . . ?

---

### Post by TheFu on 2018-08-14
You'll need to read what Dropbox said and decide.  But do you really want to use services from a company with that behavior? Your choice.

I have brute forced passwords in ZIP files many times over the decades.   There is no substitute for length.  20+ random characters and you are probably fine, if they are truly random.

---

### Post by Paddy Landau on 2018-08-14
> **Geoffrey_Arndt said:**
> … I prep them for Dropbox via encrypting using 7z AES
Sorry if I didn't make myself clear.

Dropbox won't accept files from an encrypted file system.

So, for example, ext4 running on top of LUKS, or ecryptfs on top of ext4, won't be accepted. Files running on plain ext4, without LUKS, ecryptfs, fscrypt, etc., will be accepted. If the file itself is encrypted using 7z AES, that's fine.

Dropbox also won't accept files from anything other than ext4. It won't even accept files from an NTFS partition even though it might be shared with Windows, where it is accepted!

Dropbox has explicitly (it's not an error; it's deliberate) refused to accept files on anything other than unencrypted ext4. This rules out RHEL (Red Hat Enterprise Linux), which doesn't use ext4. It rules out every company, charity, sole trader, professional, etc. in Europe because of the GDPR rules. It rules out any self-respecting organisation outside Europe because encrypted storage is de facto required. It rules out many individuals, like me, who refuse to use unencrypted storage.

 In other words, Dropbox no longer supports Linux.

So, as Geoffrey_Arndt says, with that behaviour, we can't trust the company, because it's only a matter of time before Dropbox takes the one step further to remove its Linux app.

---

### Post by Geoffrey_Arndt on 2018-08-14
Good points . . . I did just finish a brief chat with Dropbox support.   Not much clarity in their answer if "encrypted file" support will continue even for ext4 file systems (it seems that Dropbox pretty much doesn't ensure syncing for encrypted content).

Am waiting for more promised details, and will share if received.   Meanwhile, I will join with others in LinuxLand to check out alternatives.

---

### Post by David_Wright on 2018-08-15
> **Paddy Landau said:**
> Thank you for all the comments and ideas.

I've found that [pCloud]("https://my.pcloud.com/") suits my purposes best; it seems to do everything that Dropbox does, except that it supports Linux fully.

The one downside is that pCloud doesn't have a PPA.

Based on my past experiences with Dropbox competitors, one of the most important aspects (and possibly most difficult to assess) is the likely longevity of the provider.  I signed up for Copy and thought that as it was backed by a storage business it would be available for the long haul . . . . and then they shut it down.

Does anyone have views on the Strongest-of-the-Rest of the Dropbox alternatives?

---

### Post by TheFu on 2018-08-15
Self host it using F/LOSS.  Then you aren't at the whim of someone else.

Spider oak has a good rep within the Linux community.

---

### Post by ghostis on 2018-08-15
> **Paddy Landau said:**
> 

So, [FONT=lucida console]ext4[/FONT] running on [FONT=lucida console]ecryptfs[/FONT], [FONT=lucida console]fscrypt[/FONT] or LUKS won't count! Given the EU's GDPR and other reasons, this essentially means that Dropbox has given up on Linux.



LUKS operates at the block level so it seems to work fine. My Dropbox folder is on ecryptfs on Ubuntu 16.04. I get the warning when I run "dropbox start". So, I did a quick test:

```

mkdir ~/Dropbox_Image
cd ~/Dropbox_Image/

dd if=/dev/urandom of=./Encrypted_Dropbox_Image.img bs=1M count=2500
2500+0 records in
2500+0 records out
2621440000 bytes (2.6 GB, 2.4 GiB) copied, 241.55 s, 10.9 MB/s

sudo losetup /dev/loop0 ./Encrypted_Dropbox_Image.img

sudo cryptsetup --cipher aes-xts-plain64 --key-size 512 --hash sha256 --iter-time 5000 --verify-passphrase luksFormat /dev/loop0

WARNING!
========
This will overwrite data on /dev/loop0 irrevocably.

Are you sure? (Type uppercase yes): YES
Enter passphrase:
Verify passphrase:

sudo cryptsetup luksOpen /dev/loop0 dropbox_encrypted_image

sudo mkfs.ext4 -j /dev/mapper/dropbox_encrypted_image  
mke2fs 1.42.13 (17-May-2015)
Creating filesystem with 639488 4k blocks and 160000 inodes
Filesystem UUID: 45b4f779-5a44-43a0-b104-49b673cb7bef
Superblock backups stored on blocks:
    32768, 98304, 163840, 229376, 294912

    Allocating group tables: done                                                                                                                                                                                                                                                                                           
    Writing inode tables: done                                                                                                                                                                                                                                                                                              
    Creating journal (16384 blocks): done                                                                                                                                                                                                                                                                                   
    Writing superblocks and filesystem accounting information: done


mkdir ~/Dropbox_New_FS_tmp

sudo mount /dev/mapper/dropbox_encrypted_image ~/Dropbox_New_FS_tmp/

sudo chown -R  username:usergroup ~/Dropbox_New_FS_tmp/

rsync -av ~/Dropbox/ /~/Dropbox_New_FS_tmp/

dropbox stop

mv ~/Dropbox ~/Dropbox.SAVE

mkdir ~/Dropbox	

sudo umount ~/Dropbox_New_FS_tmp/

sudo mount /dev/mapper/dropbox_encrypted_image ~/Dropbox

mount | grep Dropbox
/dev/mapper/dropbox_encrypted_image on /home/username/Dropbox type ext4 (rw,relatime,data=ordered)

dropbox start

```

Now I don't get the warning.

I made a test file in the LUKS mounted tree and it appeared in the Dropbox app on my phone.

Note 1: To be clear, in this test, files are plaintext on Dropbox's servers, but encrypted on my local SSD - as they were before. Transparent encryption such that files are encrypted on Dropbox's servers is a different animal (but not hard as far as I can tell).
Note 2: I used a loopback file. You can also use a VM disk image or second physical drive.
Note 3: I have the Dropbox free plan, so a little over 2GB is fine for the file. Adjust your loopback file size accordingly.
Note 4: Change username to your username and usergroup to your user's personal group (usually these have the same name).

---

### Post by TheFu on 2018-08-15
All of this is good, but Dropbox is giving months of warning BEFORE they push the new code out.  I suspect they will try to work at the block level devices at the partition or LV level, probably attempting to increase sync performance. It wouldn't take much for them to check for any unexpected block devices or commonly encrypted devices, then choose to block them.  We won't know until the server-side code changes.

I'd hope for LUKS to work, but I'd also have alternative plans, if it doesn't.

---

### Post by Geoffrey_Arndt on 2018-08-16
Update:   [https://www.theregister.co.uk/2018/08/14/dropbox_encrypted_linux_support/](https://www.theregister.co.uk/2018/08/14/dropbox_encrypted_linux_support/)

**Update: A Dropbox spokesperson has been in touch to correct a detail, saying: "your article mentions Dropbox doesn't support encrypted versions of ext4. It would be accurate to say that Dropbox will not support ecryptfs, however it will support full disk encryption."**

---

### Post by ubname on 2018-08-16
> **Paddy Landau said:**
> Dropbox will [drop support for Linux]("https://www.dropboxforum.com/t5/Syncing-and-uploads/Dropbox-client-warns-me-that-it-ll-stop-syncing-in-Nov-why/td-p/290058") from November.



So, [FONT=lucida console]ext4[/FONT] running on [FONT=lucida console]ecryptfs[/FONT], [FONT=lucida console]fscrypt[/FONT] or LUKS won't count! Given the EU's GDPR and other reasons, this essentially means that Dropbox has given up on Linux.



I found this post on your link, it seems that some encryption will still be in support:

[ATTACH=CONFIG]280746[/ATTACH]

---

### Post by TheFu on 2018-08-16
> **Geoffrey_Arndt said:**
> Update:   [https://www.theregister.co.uk/2018/08/14/dropbox_encrypted_linux_support/](https://www.theregister.co.uk/2018/08/14/dropbox_encrypted_linux_support/)

**Update: A Dropbox spokesperson has been in touch to correct a detail, saying: "your article mentions Dropbox doesn't support encrypted versions of ext4. It would be accurate to say that Dropbox will not support ecryptfs, however it will support full disk encryption."**

Well, 18.04 drops encryptfs from the install options, so I can see why they would too.  I stopped using it when my backups didn't work correctly unless my userid was logged in. It was just too much hassle for me to bother.

---

### Post by Geoffrey_Arndt on 2018-08-16
[B]Just received this answer from tech support at Dropbox:
[/B]
"[COLOR=#2B2E2F][FONT=&quot]Thanks for reaching out.[/FONT][/COLOR]

[COLOR=#2B2E2F][FONT=&quot]I just wanted to add some additional context regarding your question. [/FONT][/COLOR]

[COLOR=#2B2E2F][FONT=&quot]If you received a notification on Linux and you are running ext4, it may be because you are also running ecryptfs. Ecrypfts is not supported.[/FONT][/COLOR]

[COLOR=#2B2E2F][FONT=&quot]Dropbox makes the security of your data our highest priority. We do support full disk encryption systems, such as LUKS for Linux users.[/FONT][/COLOR]

[COLOR=#2B2E2F][FONT=&quot]If you did not receive a notification on your Linux device, and are just encrypting files manually (not via a layered filesystem like ecryptfs) you are likely not affected by this change.[/FONT][/COLOR]

[COLOR=#2B2E2F][FONT=&quot]I hope this helps clarify. Thank you and please let me know if you have any other questions I can help with.[/FONT][/COLOR]

[COLOR=#2B2E2F][FONT=&quot]Regards,
[/FONT][/COLOR]
[COLOR=#2B2E2F][FONT=&quot]Luis"
 ...................................................

Hopefully the above info is accurate and provides more clarity for Ubuntu Dropbox users.[/FONT][/COLOR]

---

### Post by playgame382 on 2018-09-06
[https://ubuntuforums.org/showthread.php?t=2398409&p=13792361#post13792361](https://ubuntuforums.org/showthread.php?t=2398409&p=13792361#post13792361)

This is great! Will this auto mount upon login though?

---

### Post by Paddy Landau on 2018-09-06
I'm pleased to see some of the updates here. It seems as though Dropbox is having a bit of a change of heart, because originally it didn't accept LUKS.

Time will tell, of course, but still, it seems idiotic for Dropbox to drop support for file systems other than ext4. That is why I'm taking this news with a pinch of salt — it's an utterly arbitrary decision, which means that it could change for the worse at any time.

---

### Post by pretzelgal on 2018-09-07
Although slightly unorthodox, [https://zenkit.com/](https://zenkit.com/) could be an alternative.
It's Linux-friendly: [https://zenkit.com/en/blog/get-zenkit-on-any-linux-distribution/](https://zenkit.com/en/blog/get-zenkit-on-any-linux-distribution/), you can store files, the app supports Android, and it can link with Google Drive.

---

### Post by undecidable on 2018-09-10
I moved from Dropbox to Syncthing in 2016, happy with it.

It is different to Dropbox in that:
[LIST]
[*]  it is peer to peer within your own devices
[*]  you can sink multiple folders anywhere, not just your Dropbox folder.  Means it fits in with how I organise my file system.
[*]  can sync different folders with different devices
[*]  installs from the repos, is open source.
[/LIST]

It works on Android, Wz, Mac not sure about iphones.  

I wrote a detailed comparison some time ago, which might be useful:
[https://forum.syncthing.net/t/new-user-experience-comparing-syncthing-vs-dropbox/7675]("https://forum.syncthing.net/t/new-user-experience-comparing-syncthing-vs-dropbox/7675")

It doesn't include cloud backup (unless you are syncing to your own cloud)
but I treat backup separately from sync.
(I think combining them is dangerous).

It is more work to setup than Dropbox (because of the greater flexibility)
but is less annoying.

---

### Post by Paddy Landau on 2018-09-10
> **undecidable said:**
> I moved from Dropbox to Syncthing in 2016, happy with it.
I've installed and played with Syncthing, and I'm most happy with it. It's great that they have a PPA. Thank you for the recommendation.

---

### Post by undecidable on 2018-09-10
Actually in 18.04 it is now in the main repos,
though of course there is a slightly later vsn in a ppa.
I use the ppa version.

---

### Post by webmiester on 2018-09-11
Will Dropbox still work with an Android emulator like anbox?

---

### Post by Paddy Landau on 2018-09-12
> **webmiester said:**
> Will Dropbox still work with an Android emulator like anbox?
Sorry, I don't know. May I suggest that you ask on the [Dropbox forum]("https://www.dropboxforum.com/").

---

### Post by webmiester on 2018-09-13
> **Paddy Landau said:**
> Sorry, I don't know. May I suggest that you ask on the [Dropbox forum]("https://www.dropboxforum.com/").

Well, actually I'm not a Dropbox user.  I was curious because if it works, maybe we can run an Android emulator and run Dropbox there.  But then again, if the issue is the support of the file system, then there isn't much we can do, unless we force Linux to use ext4.

---

### Post by SagaciousKJB on 2018-09-17
I'm a little late to the party, so is this just effecting the attempted use of an encrypted block device to store on the cloud, and then people are mounting this through the synced folder?

Wouldn't it be possible to do this with Google Drive and one of the many sync apps available for it?  I think Google Drive is a lot cheaper than Dropbox too.

---

### Post by Paddy Landau on 2018-09-18
> **SagaciousKJB said:**
> … is this just effecting the attempted use of an encrypted block device to store on the cloud, and then people are mounting this through the synced folder?
I don't quite understand your question, sorry. Dropbox won't work on any Linux file system other than ext4, whether unencrypted or on LUKS. So, it won't work on ext4 on LVM, for example, or even on a shared NTFS partition where it does work on Windows! An entirely arbitrary decision.

> **SagaciousKJB said:**
> Wouldn't it be possible to do this with Google Drive and one of the many sync apps available for it?  I think Google Drive is a lot cheaper than Dropbox too.
Google Drive would be a great replacement if the Google Drive app were available for Linux. Unfortunately, it's available only for [Windows, Android and iOS]("https://www.google.com/drive/download/").

---

### Post by SagaciousKJB on 2018-09-18
> **Paddy Landau said:**
> I don't quite understand your question, sorry. Dropbox won't work on any Linux file system other than ext4, whether unencrypted or on LUKS. So, it won't work on ext4 on LVM, for example, or even on a shared NTFS partition where it does work on Windows! An entirely arbitrary decision.


Google Drive would be a great replacement if the Google Drive app were available for Linux. Unfortunately, it's available only for [Windows, Android and iOS]("https://www.google.com/drive/download/").

I'm guessing you mean the official app?  There's several open source ones.  google-drive-ocamlfuse seems to be really good, and is said to be backed by Google--though I don't see any official documentation of that.  It's not GUI but it's a very simple CLI.  Haven't tried it myself, still trying to figure out what everyone is talking about when they're talking about using encryption with a cloud service like this.

I guess I'm a little confused about what the problem is.  If the mountpoint you choose for dropbox is on a filesystem that's not unencrypted ext4 it won't work?

I think the example of someone else using a looped filesystem image as a block device threw me off.

---

### Post by mastablasta on 2018-09-19
spideroak is another option but it has limited free storage. however, it does support linux and is encrypted. good for storing and sharing some smaller files.

otherwise Mega ftw (unless you setup your own cloud).

---

### Post by Paddy Landau on 2018-09-19
> **SagaciousKJB said:**
> &#8230;  There's several open source ones.  google-drive-ocamlfuse seems to be really good&#8230;
Thanks, I'll have a look.

> **SagaciousKJB said:**
> If the mountpoint you choose for dropbox is on a filesystem that's not unencrypted ext4 it won't work?
Correct, although Dropbox has backtracked on LUKS. It now allows ext4 on LUKS. But absolutely nothing else will be accepted, not even ext4 on LVM on LUKS.

> **SagaciousKJB said:**
> I think the example of someone else using a looped filesystem image as a block device threw me off.
Yes, Dropbox checks for that and disallows it as well. The only reason why I can think of is that Dropbox wants to drop all support for Linux, and this is the first step.

> **mastablasta said:**
> spideroak is another option&#8230;
I've used SpiderOak for years. The problem is twofold: First, SpiderOak doesn't support synchronising with Android, which I need (same with Mega). Second, SpiderOak's synchronisation can be rather tardy, whereas I need something as responsive as Dropbox, which is almost immediate.

---

### Post by SagaciousKJB on 2018-09-21
google-drive-ocamlfuse has been working okay for me so far.  It is a little slow if you have a lot of google doc files, but you can choose to turn the downloading of those off in the options--though unfortunately they still appear in your file tree window if that matters.

What I like about it is that it mimmick's Dropbox's behavior of mounting your storage onto a virtual file-system under your file-system tree.  So if I put, "google-drive-ocalmuse /mnt/google-drive/" then I can browse my Google Drive on /mnt/google-drive as if it were my own file-system.  Files transferred or deleted are updated in real-time.

On the other hand, one popular option such as Grive2 rely on "pushes" to sync changes between your local folders and Google Drive.  A few of the other apps are said to behave more like google-drive-ocalmfuse and Dropbox, but two are non-free (Insync ($29) and overGrive ($5)) and I didn't try GoSync before I was satisfied with google-drive-ocamlfuse.

Here's a pretty comprehensive list of clients available for Google Drive on linux.

[https://www.ubuntupit.com/top-12-best-google-drive-linux-client-software/](https://www.ubuntupit.com/top-12-best-google-drive-linux-client-software/)

At first I tried creating a LUKS volume and putting that on to Google Drive, but then when I tried to run 'cryptsetup luksOpen' on the LUKS volume, it just made google-drive-ocamlfuse jump in CPU usage and then never actually setup the /dev/mapper device files.  I'm really not sure that cryptsetup was ever intended to be able to set a volume up over a serial connection like over the internet, so I decided to try something else besides deciding it wouldn't work.

Meanwhile, eCryptfs worked just fine.  I did "mount -t ecryptfs /mnt/google-drive/crypt-backups /mnt/plain-backups" so that I can transfer my files to /mnt/plain-backups and have eCryptfs encrypt and store them on /mnt/google-drive/crypt-backups.  It then leaves the directory plainly visible under /mnt/google-drive/plain-backups and allows me to encrypt filenames that are stored on the /mnt/google-drive/crypt-backups side.  It's a bit like encfs, but it runs entirely in the kernel, so you'll need to have root access to use it.  I wouldn't suggest encfs unless you're comfortable with its security vulnerabilities ( disclosed via dpkg dialog warning after installing it ).

Still though, since I pay $1.99 a month for 100 gb, it does make Google Drive quite competitive with other services even if they have better and more simplified software options available to them.

---

### Post by Paddy Landau on 2018-09-22
Thanks for all of that, SagaciousKJB.

One disadvantage of google-drive-ocamlfuse is that when you are offline, it just doesn't work, and you can't access your files. Whereas Dropbox keeps a full copy on your drive and queues the updates. That's what I really need &#8212; and only for a single file.

I don't know how to get around this limitation.

---

### Post by SagaciousKJB on 2018-09-22
> **Paddy Landau said:**
> Thanks for all of that, SagaciousKJB.

One disadvantage of google-drive-ocamlfuse is that when you are offline, it just doesn't work, and you can't access your files. Whereas Dropbox keeps a full copy on your drive and queues the updates. That's what I really need — and only for a single file.

I don't know how to get around this limitation.

Ah, I had a different type of use in mind that google-drive-ocamlfuse was suited well too.

It sounds like Grive2 would be more suited to what you want to do.  It waits until you manually "push" changes to actually upload to the Google Drive.  I think the others may have similar uses.

---

### Post by Paddy Landau on 2018-09-23
> **SagaciousKJB said:**
> It sounds like Grive2 would be more suited to what you want to do.
I tried Grive2, but I had to write a script to wait for changes and then either push them (if made on the computer) or pull them (if made on the Android). Inconvenient.

I'm currently using Syncthing, which works OK, but it has two flaws. First, it's slow to update. I can wait several minutes, even longer for it to synchronise. Second, when first logging into the computer, it won't synchronise until I open the Android app.

---

### Post by albertodl on 2018-11-01
Hello Paddy,

what did you finally settle for ?? Less than a week to go and I have not decided yet... :-(

---

### Post by Paddy Landau on 2018-11-01
> **albertodl said:**
> what did you finally settle for?
I'm using SyncThing. Its response has improved. You need to set it to automatically start when you start your phone, whitelist it in Android's battery saving, and allow for the fact that it's slower than Dropbox. It also takes a while to set up on Ubuntu initially. But, it has proven reliable.

EDIT: SyncThing doesn't use its own storage as Dropbox does. Both source and target need to be connected to the internet to work. It's not a full replacement for Dropbox.

---

### Post by Paddy Landau on 2019-07-22
News!

Dropbox restores support for other Linux file systems &#8212; well, selected ones, anyway.

[https://www.linuxuprising.com/2019/07/dropbox-brings-back-support-for-zfs-xfs.html](https://www.linuxuprising.com/2019/07/dropbox-brings-back-support-for-zfs-xfs.html)

---

