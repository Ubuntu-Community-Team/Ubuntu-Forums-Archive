---
title: "Best online back up service"
date: 2010-11-03
forum: Security
---

### Post by dogdo on 2010-11-03
At the moment i use google documents  as my online storage space but while the transport layer does use ssl im not sure if other people or google themselves can read my documents. With that in mind what is the best online backup for home use? If possible free to a degree as well with a decent upload cap-50GB at least?

---

### Post by Barriehie on 2010-11-03
I wouldn't trust any of them!  External drives are cheap and easy to use with a crontab entry and a small shell script using rsync.

---

### Post by dogdo on 2010-11-03
> **Barriehie said:**
> I wouldn't trust any of them!  External drives are cheap and easy to use with a crontab entry and a small shell script using rsync.

But i want to back up my data in a few places. I do have a external hard drive but hard drives can sometime fail.

Why dont you trust online back up services-what should i know?

---

### Post by Barriehie on 2010-11-03
> **dogdo said:**
> But i want to back up my data in a few places. I do have a external hard drive but hard drives can sometime fail.

Why dont you trust online back up services-what should i know?

No need to trust them! It's just BB getting into your business. :)  Why have a login on your machine if you're going to upload the data to someone else's box!  I use an external drive and a USB flash drive.  HD gets replaced, irregardless, every three years and I've 2 USB flash drives.  I've been carting around the same $HOME for years with a list of installed packages so it's no issue if something fails.  Might find this useful in your backup routine:
```

dpkg --get-selections | gawk '{ if( $0 !~ /.*deinstall$/) { print $0 }}' > /media/backup/packages-$(date +%m%d%y)
```

After looking at it this will do the same thing:
```

dpkg --get-selections | grep -v deinstall > /some_path/some_file

```

---

### Post by uRock on 2010-11-03
You can create an encrypted zip, then upload it. Just take care to create a backup of the encryption key so that you can restore it later.

---

### Post by noway2 on 2010-11-04
I personally use Jungledisk to backup my server. I chose this after reading several recommendations on a Linux mailing list that I subscribe. 

Jungledisk has multiple options including standard "cloud" type shared file storage (similar to Ubuntu One for example) and a remote server option where you don't have a GUI on the machine and access the controls remotely.  I think the least expensive option is about $2 (USD) a month and the server one runs $5 (USD) for up to 10 GB of storage.  After that it is a slight charge.  The billing can be handled either directly or through Amazon.com if you prefer.

Personally, if I am going to store anything that I consider to be sensitive I will encrypt it with PGP first.  I believe Jungledisk has an encrypt everything option if you so prefer.

In my opinion one real advantage of off site storage is that your information will be retrievable should a disaster strike your location and this can be good place to store things that you would need or want to help recover in such an event.

---

