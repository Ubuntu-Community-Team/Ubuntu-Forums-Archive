---
title: "Western Digital My Cloud"
date: 2015-04-06
forum: The Cafe
---

### Post by pfeiffep on 2015-04-06
I purchased subj for a single point backup for computing devices in my house. I was somewhat apprehensive in setting up Ubuntu Backup since it's advertised for Windows and Mac support (even though it runs on a Debian kernel)
The Mac portion worked flawlessly (using TimeMachine). I inched my way to Ubuntu and accessing which worked perfectly using Nautilus. Then I set up my 2 Ubuntu machines to automatically backup to My Cloud which again worked perfectly.
I'm able to use my iPhone to browse my pictures, haven't tried iTunes as yet.
After a month I still haven't set the Windows 7 installs to work so perfectly. The Smartware software provided is somewhat problematic.

I find it odd that both Ubuntu and Mac (neither rely on Western Digital software) work exactly as I expected, but the backup software supplied for Windows doesn't. Oh well, I can always manually backup the seldom used Win 7 manually. 

So much for Windows is easier - yea RIGHT!;)

---

### Post by Welly Wu on 2015-04-09
I have a Western Digital My Cloud Personal Cloud 4.0 TB NAS drive and I have a Lenovo IdeaPad Y510P running Ubuntu 14.04.2 64 bit LTS GNU/Linux and I own Codeweavers' CrossOver for Ubuntu 64 bit GNU/Linux version 14.1.0 64 bit. I installed Microsoft .NET 4.5.1 and I installed the Western Digital My Cloud software application successfully. I can access my WD My Cloud NAS drive locally using Nautilus and remotely using the WD My Cloud software application, but Nautilus has a bug that does not allow me to cut, copy, and paste from the WD My Cloud software application to Nautilus. In other words, I can not easily cut, copy, and paste from my WD My Cloud to my PC using Nautilus. I have to use the send link feature in my WD My Cloud software application and my Google Chrome or Mozilla Firefox web browser to download data from my WD My Cloud NAS drive remotely. It works, but it's not elegant. Otherwise, that's all I use and it works well enough.

---

### Post by makitso on 2015-04-09
I have the WD Personal Cloud 2TB model and use it with Win7 and Ubuntu Gnome (UG) 14.04 (mounted via NSF).  I wanted to run a VirtualBox client off the NAS but the performance was not good enough to make this practical -- even with a 1G LAN, reads are 40MBps at best.  I did note that the WIN7 client is much slower than UB.

---

### Post by pfeiffep on 2015-04-09
I don't trust the security / privacy of WD's implementation so I have disabled remote access completely. Using Nautilus on my wifi connected Dell I can copy and paste just fine from My Cloud; of course this isn't at all a duplication of yours!

---

### Post by Welly Wu on 2015-04-09
I contacted Western Digital and they told me that they use AES 256 bits to encrypt the data when it is in motion and they use AES 128 bits for data at rest. In other words, they use the Advanced Encryption Standard algorithm at 256 bits when uploading or downloading data and 128 bits for data stored on the WD My Cloud. It may use single factor authentication, but it is fairly standard in terms of security and it is safe enough for cloud access. I never had a problem with mine and I monitor all of my logs daily. It's a decent product that mostly works in GNU/Linux using WINE technology. I am hoping that Ubuntu 16.04 64 bit LTS GNU/Linux is going to fix the Nautilus cut, copy, and paste functions so it will be easier to download data from my WD My Cloud NAS drive in the future.

---

### Post by pfeiffep on 2015-04-09
> **Welly Wu said:**
> I contacted Western Digital and they told me that they use AES 256 bits to encrypt the data when it is in motion and they use AES 128 bits for data at rest. In other words, they use the Advanced Encryption Standard algorithm at 256 bits when uploading or downloading data and 128 bits for data stored on the WD My Cloud. It may use single factor authentication, but it is fairly standard in terms of security and it is safe enough for cloud access. I never had a problem with mine and I monitor all of my logs daily. It's a decent product that mostly works in GNU/Linux using WINE technology. I am hoping that Ubuntu 16.04 64 bit LTS GNU/Linux is going to fix the Nautilus cut, copy, and paste functions so it will be easier to download data from my WD My Cloud NAS drive in the future.I totally agree that it **IS** a decent product! I don't need Windows at all to effectively set up and manage My Cloud.  It backs up Mac, Ubuntu, and Windows just fine, and I only really wanted  it to have in in home single point back up solution! I've disabled all UPnP at the router and on My Cloud.

I don't think that most home based solutions are [COLOR=#ff0000]safe enough for cloud access[/COLOR]. I have no problem with WD encryption implementation ... I have a problem with the effort required to maintain a home based solution safely and securely. I'm retired from a financial enterprise internet security firm and really don't personally want the complexity of 'doing it right'. Checking  logs daily is just one aspect that I really don't aspire to any more.

---

