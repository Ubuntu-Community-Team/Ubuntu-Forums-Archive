---
title: "I downloaded a file to my 8.04 server that I want to execute..weird result."
date: 2009-04-06
forum: Server Platforms
---

### Post by Linuxwho? on 2009-04-06
I downloaded it on my windows machine and it is named :

"zcs-5.0.6_GA_2314.UBUNTU8.FRANKLIN"

I downloaded it to my server 8.04 machine with wget and when I go to list the file it says this:

The url is:
[http://sourceforge.net/project/downloading.php?group_id=224243&use_mirror=voxel&filename=zcs-5.0.6_GA_2314.UBUNTU8.FRANKLIN.tgz&a=51069948](http://sourceforge.net/project/downloading.php?group_id=224243&use_mirror=voxel&filename=zcs-5.0.6_GA_2314.UBUNTU8.FRANKLIN.tgz&a=51069948)


"**root@ubuntu:/tmp#** ls
[COLOR="DarkSlateBlue"]downloading.php?group_id=224243  files[/COLOR]
**root@ubuntu:/tmp#**

Does that mean it is still dowloading or is that the name of the file??  Why is it named something different?  How do I execute it?

I am trying to simply download the file and execute it.](*,)

---

### Post by kanikilu on 2009-04-06
To download it, you need the *direct* link, which sourceforge puts at the top of the page when you go to download a file: ```
wget http://voxel.dl.sourceforge.net/sourceforge/zimbracommunity/zcs-5.0.6_GA_2314.UBUNTU8.FRANKLIN.tgz
```

Then to extract it: ```
tar zxvf zcs-5.0.6_GA_2314.UBUNTU8.FRANKLIN.tgz
```

That should extract it to a folder, after that, though, you'll need to read the documentation or see if there is a README inside the folder, because I've never used zimbra before...

---

### Post by Linuxwho? on 2009-04-06
Thank you for opening my eyes on that one!  ):P  I am coming from a windoze environment and trying to be more aware.  :)

---

