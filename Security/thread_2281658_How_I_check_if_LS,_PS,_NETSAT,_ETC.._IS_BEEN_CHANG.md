---
title: "How I check if LS, PS, NETSAT, ETC.. IS BEEN CHANGED (HACKED)"
date: 2015-06-08
forum: Security
---

### Post by rhandy2 on 2015-06-08
How I can see if Ls, Ps, Netsat is been modified.

Where are the location of that files?

---

### Post by papibe on 2015-06-08
Hi rhandy2.

Where is 'ls':
```
$ which ls
/bin/ls

```
What package belongs to:
```
$ dpkg -S /bin/ls
coreutils: /bin/ls

```
or both at the same time:
```
$ dpkg -S $(which ls)
coreutils: /bin/ls

```
All packages come with checksums that can be verified. The simplest way to do that would be to install 'debsums':
```
sudo apt-get install debsums
```
Then you can do:
```
debsums -c coreutils
```
This is all from the point of view of package's integrity. There are more tools to track even more stuff depending on how deep you want to go.

I hope it helps. Let us know how it goes.
Regards.

---

### Post by rhandy2 on 2015-06-09
Hello

Thanks for all your help.

I do all things you said, but when I do  :
>  debsums -c coreutils

I don´t have any answers.

It should be OK ??? I think!!!

---

### Post by papibe on 2015-06-09
> **rhandy2 said:**
> It should be OK ??? I think!!!
Yes.

The '-c' option only reports changed files. If none were modified, nothing to report ;)

Regards.

---

### Post by fugu2 on 2015-06-11
Just to give my 2 cents: these files should be checked on a separate computer from the one in question, one that your sure hasn't been tampered with. The only way to be truly sure

---

### Post by HermanAB on 2015-06-11
BTW, look into tools like tripwire.
[http://www.linuxjournal.com/article/8758](http://www.linuxjournal.com/article/8758)

---

### Post by rhandy2 on 2015-06-11
Thanks!!!

---

### Post by rhandy2 on 2015-06-12
Fugu2

How I can check it?

I save the Ls, Ps files to other machine, and after how I check. Sorry I dont understand?

---

### Post by Habitual on 2015-06-12
[tripwire "how to" ]("http://ubuntuforums.org/showthread.php?t=2235300")

---

### Post by fugu2 on 2015-06-15
> **rhandy2 said:**
> How I can check it?


from the "good" machine 
```

$ cd dir_of_suspect_files/
$ md5sum ./ls
$ sha1sum ./ls
$ md5sum ./ps
$ sha1sum ./ps
...

```

then compare these checksums with known stock checksums (or post the checksums here, maybe someone else can verify they are the same)

---

### Post by rhandy2 on 2015-06-18
Many Thanks !!!!

---

