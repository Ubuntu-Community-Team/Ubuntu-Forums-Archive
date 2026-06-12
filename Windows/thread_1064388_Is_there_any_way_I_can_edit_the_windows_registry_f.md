---
title: "Is there any way I can edit the windows registry from ubuntu live CD?"
date: 2009-02-08
forum: Windows
---

### Post by JohnParker on 2009-02-08
Hi, I have force booted the windows partition from the live CD, I could also do it from the working linux partition but I find everything much smoother on the live cd. So when I changed drive J to C in windows I lost all my user Icons, so does anyone know where I can access my Hkey_Local_Machine to mark it as J again? Or, would it be even easier to boot into my linux partition, force mount, and run regedit?
Windows XP SP3 Btw.

---

### Post by ju2wheels on 2009-02-08
Theres a registry-tools package in the repository you can look at, have no clue how well it works or if it works at all.

Alternatively you can try your luck by running regedit.exe (the one on your windows partition) using Wine...

---

### Post by Dougie187 on 2009-02-08
Yeah i think wine should work. Even if you can't directly edit your registry with your windows partition's version of regedit, you should be able to run the regedit that comes with wine and import your registry and edit it that way.

---

### Post by JohnParker on 2009-02-09
The regedit works fine with wine but does not save its changes to the registry, can I get a link to the ubuntu/wine version?

---

### Post by ju2wheels on 2009-02-09
> **JohnParker said:**
> The regedit works fine with wine but does not save its changes to the registry, can I get a link to the ubuntu/wine version?

? what command did you use to start regedit. There's no "Ubuntu" version of regedit, theres only regedit that comes with wine in your ~/.wine/drive_c/windows/ directory and the regedit on your windows partition, both of which you should be able to start up using wine.

As I said before the other option is to try the "registry-tools" package installable through Synaptic or:

```

sudo apt-get install registry-tools

```

---

### Post by HermanAB on 2009-02-09
Wait!!!

Use BartPE to do this: [http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)

Cheers,

Herman

---

### Post by JohnParker on 2009-02-09
I just used (in the terminal) wine (dragged regedit.exe here) and it loaded up fine, but when I change C to J it doesnt save the changes, and changes itself back.

Also registry-tools isn't found.

---

### Post by JohnParker on 2009-02-09
> **HermanAB said:**
> Wait!!!

Use BartPE to do this: [http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)

Cheers,

Herman

I can't, I can't get into windows to make the CD itself.

---

### Post by JohnParker on 2009-02-09
Im considering wiping the entire drive(both partitions and reinstalling both, dont have much on either partitions anyway.
Edit Triple post :S

---

### Post by ju2wheels on 2009-02-09
> **JohnParker said:**
> I can't, I can't get into windows to make the CD itself.

Why the need to do that if you can get into Linux you can do it from there, all the tools you need are installed by default. Brasero....


Edit: Although to be quite honest I dont see how a live Windows cd is going to be any more helpful at solving your problem than booting into Linux will be.

---

### Post by tturrisi on 2009-02-11
[http://home.eunet.no/pnordahl/ntpasswd/](http://home.eunet.no/pnordahl/ntpasswd/)

---

