---
title: "How to rescue SVN repo from dead server"
date: 2009-08-09
forum: Server Platforms
---

### Post by twidget on 2009-08-09
Hi,
I'm trying to figure out if there is a way to rescue the data from an old svn repo. my old server's motherboard went away and the drives will not boot with a new motherboard. the other problem is that I've had this shelved for a while and unfortunately i didn't write down any of the passwords. either way I can mount the drives and browse the file system using puppy Linux but I can't seem to find where svn hid my actual files. I don't really care about preserving the repo structure. mostly I just want to make sure that there isn't anything I don't have backups of on there before I wipe the drives and use them for my next attempt at a home server. any help would be appreciated.

---

### Post by shizakapayou on 2009-08-09
You won't see your actual files (ie, if sample.txt is in the repo, you won't see sample.txt in the server's filesystem).

In the past, I've copied the entire repository path from the old server, say /home/svn/repo.  Then on the new server, create a new repository by the same name, which will create default files in the repo path.  Finally, overwrite the default files in the new repo with your old repo, and you'll be able to access your repository just like it was.

---

### Post by twidget on 2009-09-04
problem is I don't remember my password/username for that server and the SVN repo on it. Is there any way of getting the data back without login info? all I have left of the old server is a drive immage at this point.

---

### Post by hessiess on 2009-09-04
Mount the drive on a live cd or linux install on a second computer and copy the root directory of the repository to the new servers SVN repo location. Assuming the drive wasent encripted doing this will bipass the need for login info. Idealy you should periodically svnadmin dump the repository as the on-disk format sometimes changes, which can leave repos un useable if you use a newer version of SVN.

---

### Post by holiday on 2010-10-16
> **shizakapayou said:**
> You won't see your actual files (ie, if sample.txt is in the repo, you won't see sample.txt in the server's filesystem).

In the past, I've copied the entire repository path from the old server, say /home/svn/repo.  Then on the new server, create a new repository by the same name, which will create default files in the repo path.  Finally, overwrite the default files in the new repo with your old repo, and you'll be able to access your repository just like it was.

Thanks. That worked great.

$ svnadmin create /var/svn/repos/treasure
$ cp -r treasure/* /var/svn/repos/treasure

and then

$ svn list file:///var/svn/repos/treasure

And there it all was back again. 

Thank you very much.

---

