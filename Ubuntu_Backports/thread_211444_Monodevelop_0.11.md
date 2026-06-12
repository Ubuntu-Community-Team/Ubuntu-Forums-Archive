---
title: "Monodevelop 0.11"
date: 2006-07-08
forum: Ubuntu Backports
---

### Post by jvpgomes on 2006-07-08
Hi!

I cannot find Monodevelop 0.10 in the repositories.

So I tried to install it from the the source files.

But I'm having a problem that I don't understand.

When I do the make instrution I have this error:

(...)
fig/../../lib/mono/gtk-sharp-2.0/atk-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gdk-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gtk-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/art-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gnome-vfs-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/glib-sharp.dll
make[2]: *** [../../build/AddIns/MonoDevelop.SourceEditor.dll] Error 134
make[2]: Leaving directory `/home/joao/monodevelop-0.11/Extras/MonoDevelop.SourceEditor'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/joao/monodevelop-0.11/Extras'
make: *** [all-recursive] Error 1
joao@pc-j:~/monodevelop-0.11$ 


Can someone help me?

Please!

Thank you!

---

### Post by PlatinumPlus on 2006-07-10
Monodevelop 0.10 is in the repos but not 0.11 ;)

---

### Post by jvpgomes on 2006-07-10
It a mistake. I wanted to say 0.11.
The version 0.11 is not in the repositories, so I tried to install it, but I had those erros.

:(

---

### Post by tormentum on 2006-08-18
where does one find out who the maintainer for that particular package is?  i'm fairly new to the whole debian based distro (ex slackware here) so i'm not sure how the whole repository maintenance thing works.  Any help'd be much appreciated.

---

### Post by viraptor on 2006-08-30
Someone interested in 0.11 backporting? This probably should be notified: [https://launchpad.net/products/dapper-backports/+bug/49753](https://launchpad.net/products/dapper-backports/+bug/49753)
Reject reason is not valid, as 0.11 landed in Edgy.

---

### Post by mlind on 2006-08-30
Reopen [https://launchpad.net/products/dapper-backports/+bug/49403](https://launchpad.net/products/dapper-backports/+bug/49403)
bug if you want developers to see your request, 49753 is a duplicate.

Backporting monodevelop 0.11 is very tough task, it depends on libraries that are not available on Dapper if I remember correctly.
I recall that getting monodevop to compile required newer version of the whole mono runtime environment..

---

### Post by Farny on 2006-09-03
I'd like to second an effort for a backport.  The .NET 2.0 and stetic features are pretty desirable.

I just finished setting up a machine with dapper (it had FC5 on it) and was in the middle of a project using MD 0.11.  It was my bad for not realizing I would be missing key features by stepping back a point release, but how do I go about helping with the backport effort (or do I just add my vote here and get out of the way)?

---

### Post by viraptor on 2006-10-05
João Pinto made a package of 0.12 for dapper. I haven't tested it you yet, but it's just being downloaded from [http://www.getdeb.net/category.php?id=30](http://www.getdeb.net/category.php?id=30)
Have fun, and thanks again João!

---

### Post by jdong on 2006-10-05
There is a repository with the Edgy mono stack backported to Dapper as long as Edgy versions of most of the mono packages, including monodevelop.... I can't find it at the moment, slomo on #ubuntu-motu told me about it. I'll try to dig it up.

---

### Post by viraptor on 2006-10-05
Please do - upgraded mono stack would be also nice to have :)

---

### Post by squimmy on 2006-10-09
The deb [here]("http://www.getdeb.net/category.php?id=30") seems to work just fine, unless i´m missing some super bug or something.

---

### Post by Ba|der on 2006-10-12
I tried the deb pach from the previous post and got error about missing gtk-sharp. I'm running Ubuntu 6.06. Any suggestion on how to get gtk-sharp installed or another way to get monodevelop up and running?

---

### Post by viraptor on 2006-10-12
apt-get install gtk-sharp

---

### Post by Ba|der on 2006-10-13
Well, I did actually trie that. Ubuntu said no such package available. I had also added the packports repository=NoGo.

Update: 
After a clean reinstall today monodevelop installed just fine :-D

---

