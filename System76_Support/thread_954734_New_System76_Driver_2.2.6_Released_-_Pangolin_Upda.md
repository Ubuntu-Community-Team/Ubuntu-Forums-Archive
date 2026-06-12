---
title: "New System76 Driver 2.2.6 Released - Pangolin Updates"
date: 2008-10-21
forum: System76 Support
---

### Post by crichell on 2008-10-21
System76 Driver 2.2.6 has just been released to the repositories. This releases fixes a couple Pangolin Performance (panp4) bugs and adds support for new models.

For good measure run the following two commands in your terminal to add the System76 repository and System76 repository signing key:

```
sudo wget http://www.planet76.com/sources.list.d/system76.list -O /etc/apt/sources.list.d/system76.list
```
```
wget -q http://planet76.com/repositories/system76_dev.pub -O- | sudo apt-key add - && sudo apt-get update
```

Version 2.2.6

 * Fix panp4 mic and sound after resume LP #264516		
 * Add System76 Bonobo Pro (bonp2)
 * Add System76 Serval Pro (serp5)
 * Fix system designation for one Pangolin panv2 where the MB had been replaced
 * Update Linux UVC code
 * Add Ubuntu Intrepid to System76Driver.py (no system patches applied yet)

Only customers with the new Pangolin Performance (panp4) need to run the driver. After the updated driver has been installed go to System > Administration > System76 driver and click the "Install Drivers" tab. Click install. After your next reboot the internal mic and sound after resume from suspend will work.

On Tuesday, Oct. 28th we'll release a new driver with Ubuntu 8.10 "Intrepid Ibex" support.

---

### Post by pak33m on 2008-10-21
Carl,

I just ran:

```
sudo aptitude update
```

And I received he following error:

```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://planet76.com ./ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 176A5C84ED67C9ED

W: Failed to fetch http://planet76.com/repositories/./Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

```

Then I read this post.  I ran what was posted to update the key but do I install the driver but not run the driver if since I have a gazv4?

Jimmy (pak33m)

---

### Post by thomasaaron on 2008-10-22
Yes, you can install and run the driver.

---

### Post by greg_g on 2008-10-22
pak33m, be sure to install the new gpg key, I think it changed as I got the same error.

---

### Post by pak33m on 2008-10-23
Hey guys,

Thank you for the info.

After the System76 2.2.6 driver install and a reboot it seems that my wireless went bye-bye.  That is until I reverted back to the System76 2.2.5 driver.

I just wanted to let you all know.

Did you need me to collect any info about this?

---

### Post by thomasaaron on 2008-10-24
pak33m,

Can you check that again, please. I think you might have something else going on for two reasons...

1. Wireless works out of the box with Ubuntu. We add no patches for it.
2. Even if we did add patches for it, any patches installed by 2.2.6 would not be *removed* by 2.2.5.

---

