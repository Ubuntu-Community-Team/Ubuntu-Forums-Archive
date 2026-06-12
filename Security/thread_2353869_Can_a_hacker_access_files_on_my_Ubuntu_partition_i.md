---
title: "Can a hacker access files on my Ubuntu partition if my Windows partition gets hacked?"
date: 2017-02-25
forum: Security
---

### Post by John_Patrick_Mason on 2017-02-25
Suppose my Windows partition gets hacked and a hacker quietly installs a backdoor on Windows, can that hacker then access my files on my Ubuntu partition when I boot into Ubuntu?

---

### Post by bearlake on 2017-02-25
> **John_Patrick_Mason said:**
> Suppose my Windows partition gets hacked and a hacker quietly installs a backdoor on Windows, can that hacker then access my files on my Ubuntu partition when I boot into Ubuntu?

I wouldn't think so.

Now if you were booted into Windows and a hacker had a back door into Windows, then he could access files anywhere on the drive(s).

I'm sure we will see many post here shortly adding to this one way or another. ):P

---

### Post by John_Patrick_Mason on 2017-02-25
> Now if you were booted into Windows and a hacker had a back door into  Windows, then he could access files anywhere on the drive(s).

You mean the C: drive, or any other drive on my Windows partition, right?

Now let's suppose for the sake of the argument that this hacker installed a keylogger program, that records any keystroke I type, including any password I type when I first login to my Windows partition. And let's also suppose for the sake of the argument that the vulnerable password I use to login to my Windows partition is the same password I use to login to my Ubuntu partition, wouldn't the hacker then be able to access the files on my Ubuntu partition now that he knows my Ubuntu partition password?

---

### Post by bearlake on 2017-02-25
They wouldn't need a password to go from one OS to another if they gain total access into your Windows OS or visa versa.

You want to be 100% safe, then stay off the Internet.

---

### Post by John_Patrick_Mason on 2017-02-25
I guess so long as my Windows partition is free of malware, and I only boot into my Ubuntu partition to access the internet, I should be good, right?

Just curious, do you know where I have to go to access my Ubuntu partition files when booted into my Windows partition? I know anybody can access your Windows files from Ubuntu, so it kinda makes sense that you can do the same from Windows, I'm just not sure where I have to go in order to access them.

---

### Post by Irihapeti on 2017-02-25
To access your Ubuntu partition(s) from Windows, you need to install special drivers so that Windows can recognise them. If you've not been able to see your Ubuntu partition from Windows, that would be why.

Of course, a hacker can still trash your Ubuntu partition by formatting the entire disk, even if he/she can't read the individual files.

---

### Post by John_Patrick_Mason on 2017-02-25
Wow, you learn something new everyday. Any idea where I would need to go to find some of these drivers for *my* hardware? Do they have like a specific name?

---

### Post by Irihapeti on 2017-02-25
It's a looooooonng time since I used them, so I'm not sure I remember the name. You could try searching for "ext4 drivers for Windows", or something like that.

Back when I was using them, there was one that would only work with ext3 filesystems, but it seemed pretty reliable to me. There were others that would handle ext4 filesystems, but they were read-only. What the deal is nowadays, I wouldn't know.

---

### Post by John_Patrick_Mason on 2017-02-25
I guess it would make sense that they would be called ext4 drivers, given that the Ubuntu partition is formatted using the ext4 filesystem. That being said, I don't intend installing any of them since they would be a security risk. Thank you all for answering all of my questions, I'll leave this thread open for a couple more days for anybody else who would like to contribute to the conversation.

---

### Post by kevdog on 2017-02-26
I think it would be foolish to have a sense of security that since the Linux is on a different partition with a different filesytem, the data couldn't be stolen.  I'm no expert in security -- far from it.  However if the main partition like the C: drive was hacked, depending on the hack, what's not to think they couldn't just download the data on the partition by copying it or using something like the dd utility which doesn't need a filesystem driver.  Accessing is a tricky word -- since does this mean they can access the live data, or could this apply to copying the data, and then accessing it not in real time.  There are a lot of theoretical scenarios which data on the other partition wouldn't be safe.  I say theoretical because I have no idea how prevalent or easy it would be to deploy these theoretical hacks.

---

### Post by kurt18947 on 2017-02-26
I think (certainly I'm no expert) that it might be possible using the default dual boot configuration to see an ext* configuration from a Windows install. Being able to read files on that ext* partition would be another matter as mentioned. I have used a boot manager that gives control over what is visible/accessible between operating systems. I have used the predecessor of this:

[http://www.terabyteunlimited.com/bootit-bare-metal.htm](http://www.terabyteunlimited.com/bootit-bare-metal.htm).

Note that it doesn't work with UEFI. Another way to limit access to intruders would be to encrypt the  /home or entire partition. Yes a keylogger might yield passwords but it seems like someone would have to be willing to devote quite a lot of resources to penetrate those multiple layers.

---

### Post by SeijiSensei on 2017-02-26
Ext2 Driver for Windows:  [https://sourceforge.net/projects/ext2fsd/files/Ext2fsd/0.68/](https://sourceforge.net/projects/ext2fsd/files/Ext2fsd/0.68/)

Supports *[some]("http://www.ext2fsd.com/?page_id=25")* ext3 and ext4 features.  Use with caution.  Read the [documentation]("http://www.ext2fsd.com/?cat=3").

---

### Post by bashiergui on 2017-03-09
> **John_Patrick_Mason said:**
> Suppose my Windows partition gets hacked and a hacker quietly installs a backdoor on Windows, can that hacker then access my files on my Ubuntu partition when I boot into Ubuntu?
No. Windows malware will run on Windows while Windows is running. If you have booted into Ubuntu then Windows isn't running therefore neither is its malware. 

You should consider running Windows in a virtual machine on a linux host. You can create a "snapshot" of a known, clean instance of Windows (like right after installation and updatingis done and all programs are installed). Then do whatever it is that's getting you owned all the time and revert to that clean snapshot when you're done.

---

