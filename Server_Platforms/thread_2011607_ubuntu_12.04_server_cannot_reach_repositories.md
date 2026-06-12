---
title: "ubuntu 12.04 server cannot reach repositories"
date: 2012-06-27
forum: Server Platforms
---

### Post by Cfhs_1 on 2012-06-27
Hello everyone,

I'm finally upgrading my servers froms 10.04 to 12.04, but I've ran into an issue. I can't reach and of the sources. which means I can't update, or install new software. I've determined that it's not a problem with my connection, because I can freely ping any website, and get normal responses. can someone help me resolve this issue?

thanks,
NCB

---

### Post by drmrgd on 2012-06-27
What is the output of (just to get an idea of the error you're seeing):

```
sudo apt-get update
```

Seems like some people are having problems with the default Ubuntu repositories lately.  You might try changing to one of the mirrors to see if it helps.  Just head over to this site:

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

choose a mirror that seems close to you, and replace the URL in your /etc/apt/sources.list with that URL.  I'd recommend backing up your current sources.list file in case you make a mistake or want to quickly change back.  I've been having some good results with the Argonne National Lab mirror, if it's any help to you.

---

### Post by Cfhs_1 on 2012-06-27
> **drmrgd said:**
> What is the output of (just to get an idea of the error you're seeing):

```
sudo apt-get update
```

Seems like some people are having problems with the default Ubuntu repositories lately.  You might try changing to one of the mirrors to see if it helps.  Just head over to this site:

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

choose a mirror that seems close to you, and replace the URL in your /etc/apt/sources.list with that URL.  I'd recommend backing up your current sources.list file in case you make a mistake or want to quickly change back.  I've been having some good results with the Argonne National Lab mirror, if it's any help to you.

When I run apt-get update I don't get an error, it starts to download like normal, then it just freezes at 1%. The only way to exit it is to use CTRL + C

In the sources.list file, do I have to change all the URLs, or can I just comment them out, and add the new one below?

---

### Post by Cfhs_1 on 2012-06-29
Bump!!
Can anyone provide help?

---

### Post by southerngeek on 2012-06-29
Yes, you can just comment out the lines you are replacing. Although as drmrgd said it would probably be a good idea to backup your current sources.list, in case you mess something up (it happens to the best of us!) Can you post your sources.list here, just out of curiosity?

---

### Post by Cfhs_1 on 2012-06-29
> **southerngeek said:**
> Yes, you can just comment out the lines you are replacing. Although as drmrgd said it would probably be a good idea to backup your current sources.list, in case you mess something up (it happens to the best of us!) Can you post your sources.list here, just out of curiosity?

It's just a stock standard sources.list, I have made no changes to it. If it's of any interest, I had this same problem when I installed ubuntu 12.04 on my two desktop computers. I had to switch to one of the mirror servers in the settings before I could update or install anything.

---

