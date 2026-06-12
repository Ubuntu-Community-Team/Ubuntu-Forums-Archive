---
title: "weird permissions issue on dapper"
date: 2006-08-02
forum: Server Platforms
---

### Post by drashkeev on 2006-08-02
Hi,

I'm worried that there may be a problem with the sudo command on ubuntu. I have installed dapper a week or so ago, and was very pleasantly surprised as to how well everything worked and fit together. As I was customizing my folder view in nautilus, however, I noticed that for some reason /usr was not owned by root, but by my regular user. I was surprised at this. Furthermore, /opt, and what's worst /etc, all seemed to have the permissions messed up. Worrying, I went in and made sure everything was ok. It was. Apparently, the entire path of certain programs I would install manually, such as XGl, or cedega, were changed to my user. The only way I can think of this happening is if sudo gave me root access, but never actually changed my uid. i.e. a bug. I tried to look for something of the sort online, but could find nothing of the sort with a few google searches. Is there something obvious that would cause this? Should I be extremely careful with using the sudo command?

I changed the directory permissions back with chown.

--Dmitry

---

