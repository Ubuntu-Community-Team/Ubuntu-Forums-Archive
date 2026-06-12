---
title: "All of /home is gone! Please help!"
date: 2010-07-24
forum: Security
---

### Post by feedmecereal on 2010-07-24
I started getting some sort of error when I logged in saying "Could not update ICEauthority file." I tried to solve this problem myself by Googleing around and I ran across a message that said to type the following command if /home is encrypted:

```
sudo chomd 700 /home/danny
```

I did that and when I logged in I noticed that everything in /home was gone! I think it is still there somewhere because there still seems to be about 500gb of hard drive space that something seems to be filling. It must be my old profile, right?

Please help!

---

### Post by feedmecereal on 2010-07-24
Ok, I just installed Graphical Disk map and I see a lot a space taken up by .ecryptfs/danny/.Private. I hope that's a good thing.

---

### Post by prodigy_ on 2010-07-24
Don't worry, your home directory isn't gone (at least chmod command alone can't delete anything).

Try ```
chmod 755 /home/danny
``` to revert the changes you made earlier.

---

### Post by Joe of loath on 2010-07-24
> **prodigy_ said:**
> Don't worry, your home directory isn't gone (at least chmod command alone can't delete anything).

Try ```
chmod 755 /home/danny
``` to revert the changes you made earlier.

You may have to ```
sudo chmod 777 /home/danny
``` first, as otherwise you won't be able to modify it as yourself.

---

### Post by feedmecereal on 2010-07-24
That didn't work.

---

### Post by feedmecereal on 2010-07-24
That didn't work either! I tried "chmod 755 /home/danny" because I thought I typed it wrong. Did I screw something up?

---

### Post by feedmecereal on 2010-07-24
I meant to type: I tried "chmod 755 /home/danny" **twice**.

---

### Post by CharlesA on 2010-07-24
It would have just changed the permissions to what they were supposed to be.

What does this return?

```
ls -ld /home/danny
```

---

### Post by feedmecereal on 2010-07-24
> **CharlesA said:**
> It would have just changed the permissions to what they were supposed to be.

What does this return?

```
ls -ld /home/danny
```

```
danny@danny-desktop:~$ ls -ld /home/danny
drwxr-xr-x 30 danny danny 4096 2010-07-24 10:06 /home/danny

```

---

### Post by CharlesA on 2010-07-24
Those are the correct permissions. Are you able to access the home directory by typing this:

```
ls /home/danny
```

---

### Post by feedmecereal on 2010-07-24
Yes, that seems to be the default profile, but I want my old profile back. My old profile was the one that was encrypted and still seems to be on the hard drive somewhere. I think I can still see its remains when I launch Graphical Disk Map.

---

### Post by CharlesA on 2010-07-24
I guess I am confused. If you chose to encrypt your home directory, it should be unencrypted and accessible when you login.

See [here]("http://www.cyberciti.biz/faq/ubuntu-mounting-your-encrypted-home-from-livecd/") if you want to try to recover the data from it.

---

### Post by bacardiandwatermelon on 2010-07-24
> **Joe of loath said:**
> You may have to ```
sudo chmod 777 /home/danny
``` first, as otherwise you won't be able to modify it as yourself.

I was just going to add that you will probably need to add -R so it recurses all files within the danny folder...

i.e.
sudo chmod 777 /home/danny -R
and then
sudo chmod 755 /home/danny -R

---

### Post by feedmecereal on 2010-07-24
> **bacardiandwatermelon said:**
> I was just going to add that you will probably need to add -R so it recurses all files within the danny folder...

i.e.
sudo chmod 777 /home/danny -R
and then
sudo chmod 755 /home/danny -R

```
danny@danny-desktop:~$ sudo chmod 777 /home/danny -R
[sudo] password for danny: 
chmod: cannot access `/home/danny/.gvfs': Permission denied

```

---

### Post by feedmecereal on 2010-07-24
Maybe this problem was caused by something else. Before I ran into this, I was having a problem starting GNOME. I starting having a problem that is described in this thread [http://ubuntuforums.org/showthread.php?t=949750](http://ubuntuforums.org/showthread.php?t=949750)

I don't know what commands I executed in the CLI because the history seems to be erased too. If anyone can use this info to help then I would greatly appreciate it.

---

### Post by feedmecereal on 2010-07-24
On second though, I'm almost certain I executed these commands:

> chown danny:danny /home/danny/.ICEauthority
chmod 644 /home/danny/.ICEauthority
exit

---

### Post by feedmecereal on 2010-07-24
I have an encrypted /home and I have a problem that I belive may be related to Ubuntu's encryption.

Recently, GNOME would not load and I received some error messages. They said something like "Could not update ICEauthority file" and "There is a problem with the configuration server." I Googled around and I'm pretty sure I enter these commands in recovery mode:

```
chown danny:danny /home/danny/.ICEauthority
chmod 644 /home/danny/.ICEauthority
exit
```

Then, I could log in but none of my files or settings had loaded. It seemed that Ubuntu had just loaded the default profile that it loads on a new install.

The good news is that it seems that something of my old profile still exists because I installed Graphical Disk Map and scanned my entire file system and there appear to be a large number of files under .ecryptfs/danny/.Private.

I've been told to try some of the following commands to no avail:
```
sudo chmod 777 /home/danny

```
```
sudo chmod 777 /home/danny -R

```
```
sudo chmod 755 /home/danny
```
```
sudo chmod 755 /home/danny -R
```

Please help me. I'm pretty desperate. I've been using Ubuntu for a few years now but I'm not much of an expert at the CLI.

---

### Post by feedmecereal on 2010-07-24
I just thought of something: I may done this:
> sudo chmod 700 /home/danny
I'm not sure if that's important or not?

---

### Post by Joe of loath on 2010-07-24
Haven't you already got a thread on this?

Anyway, try them in this order:

```
sudo chmod 777 /home/danny
```
```
chmod 700 /home/danny
```

---

### Post by CharlesA on 2010-07-24
> **Joe of loath said:**
> Haven't you already got a thread on this?

Yup, it's right here: [http://ubuntuforums.org/showthread.php?t=1537937](http://ubuntuforums.org/showthread.php?t=1537937)

---

### Post by feedmecereal on 2010-07-24
> **Joe of loath said:**
> Haven't you already got a thread on this?

Anyway, try them in this order:

```
sudo chmod 777 /home/danny
```
```
chmod 700 /home/danny
```

That didn't work.

And yes, I have another thread on this. I thought I might get better luck starting over in the security board though.

---

### Post by CharlesA on 2010-07-24
Did you try recovering the data from a livecd as the link I posted earlier said?

---

### Post by feedmecereal on 2010-07-24
> **CharlesA said:**
> Did you try recovering the data from a livecd as the link I posted earlier said?

I tried the LiveUSB and I typed ecryptfs-mount-private and I got back: 
```
ERROR: Encrypted private directory is not setup properly

```

---

### Post by cariboo on 2010-07-24
Please don't create multiple threads on the same subject, I have merged your two threads.

---

