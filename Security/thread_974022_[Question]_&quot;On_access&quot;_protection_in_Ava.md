---
title: "[Question] &quot;On access&quot; protection in Avast"
date: 2008-11-07
forum: Security
---

### Post by shatterblast on 2008-11-07
[Please no debates concerning anti-virus.]

Hello, I'm a strong believer in open source and Java, but I'm still an amateur regarding Linux in general.  Ubuntu seems strong to me for that purpose.

So far, I have come across clamd and the "avast4workstation" package in Synaptic for a memory-resident daemon for AV.  At least, the Avast package says "on access," which makes me think it loads a daemon of some sort when installed.  I would like to confirm the name of the daemon, but I'm not too sure how to check.  I know a little, like something related to "grep."

I'm just curious if someone might know a little more about the package.  Avast.com doesn't give details from what I can find.  I'm just hoping of at minimum of working with a command-line item.

Thanks for your efforts and / or troubles.

---

### Post by daleus on 2008-11-07
Hi shatterblast, welcome to the forum.

I think its 'avastd' for the avast4workstation daemon, but I'm not too sure as I have never used it.

Good luck :)


*Edit, and as for how I found that, I'll be honest, I googled it.

---

### Post by shatterblast on 2008-11-07
I appreciate the response.  I'll look into it when I get home.  I think it also crossed my mind to check the properties of the package in Synaptic, but I'm not sure if it will tell me about a ".avast" folder.

---

### Post by cariboo on 2008-11-07
Another way to check what services and programs are running is to use **ps**, for example I prefer:

```
ps ax
```

You can also use grep in conjunction with the above command:

```
ps ax | grep avast
```

This will show if there is any daemon running with all or part of avasst in its name running.

for more info on ps check:

```
man ps
```

Jim

---

### Post by persistentstubborn on 2008-11-07
> **cariboo907 said:**
> Another way to check what services and programs are running is to use **ps**, for example I prefer:

```
ps ax
```

You can also use grep in conjunction with the above command:

```
ps ax | grep avast
```

This will show if there is any daemon running with all or part of avasst in its name running.

for more info on ps check:

```
man ps
```

Jim

Or, for us lazies

```
ps auxww | grep WHATEVERYOULOOKFOR
```

Also

```
sudo apt-get install pstree
```

And then

```
your@pc:~$pstree
```

---

