---
title: "When will Thunderbird 2 hit the repos?"
date: 2007-05-16
forum: Repositories &amp; Backports
---

### Post by Old Pink on 2007-05-16
Will Thunderbird 2 ever hit the Feisty repos? If so, when?

Or are we waiting until Gutsy for this one? 

I have already upgraded, just a consideration

Matt

---

### Post by balloons on 2007-05-16
you can get a deb for it here.

[http://ubuntu.iuculano.it/dists/feisty/thunderbird/](http://ubuntu.iuculano.it/dists/feisty/thunderbird/)

---

### Post by Old Pink on 2007-05-17
I wish I'd known that before I upgraded manually. :lol: 

Now I'm installing thunderbird using the sources over my manual installation, I have no idea of the result here. 

Actually. Having done it manually helps. I'll Trash the /opt/thunderbird file, install from repo, and then if all is well, delete the trash file.

Thing is, I like having Synaptic display the right version numbers, I hated having 2.0.0.0 installed and it showing 1.5. :lol:

---

### Post by MiKom on 2007-05-18
So, is there any chance for 2.0 in feisty? Why we have to wait for new dist upgrade to have newer versions? I think that 1.5 and 2.0 aren't so different that 2.0 need serious testing.

---

### Post by mlind on 2007-05-19
> **MiKom said:**
> So, is there any chance for 2.0 in feisty? Why we have to wait for new dist upgrade to have newer versions? I think that 1.5 and 2.0 aren't so different that 2.0 need serious testing.

It will probably appear in feisty-backports once gutsy's version has been tested more.
I also backported thunderbird from gutsy's archive to feisty.

Repository is
```

deb http://www.telemail.fi/mlind/ubuntu feisty main

```
To get the public signing key
```

wget http://www.telemail.fi/mlind/ubuntu/937215FF.gpg -O- | **sudo** apt-key add -

```

---

### Post by DizzyTech on 2007-05-20
This looks like a very stable repo, and looks like it will work with Gutsy!  It even has Pidgin!  It even has upgrade packages, so no more GAIM+Pidgin at the same time!

Thanks!

---

### Post by hexion on 2007-06-08
Thanks mlind, I was already using your repository for font's related packages but didn't noticed there was a main section too...

Just deleted my /opt/thunderbird and installed your debs. Just one issue.. your "thunderbird-locale-es-es" package doesn't work well. I had to install the .xpi file manually.

---

### Post by DJMatty on 2007-06-25
Hi mlind

I'm a bit of a linux newb, I've got thunderbird installed from the standard feisty repository, added your repository, and now in synaptic I have a mozilla-thunderbird package (a transition package) but when I select it and choose mark for upgrade it says "Depends: thunderbird  but it is not installable" and I can't find a "thunderbird" package...

Am I doing something wrong? Do I need another repository adding to get the thunderbird package?

Thanks

Matt

---

### Post by DJMatty on 2007-06-25
Heh, no worries, I added the repo at the top of the post and now it's letting me upgrade.

Thanks

Matt

---

### Post by mlind on 2007-06-25
> **DJMatty said:**
> Heh, no worries, I added the repo at the top of the post and now it's letting me upgrade.

Thanks

Matt

yeah, I somehow managed to remove the thunderbird binary from my repository when I just wanted to remove the huge source tarball to save some space. I just reuploaded it back. oops.

---

### Post by nanotube on 2007-06-26
you can also try the [ubuntuzilla script]("http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla") to install the official mozilla build.

---

### Post by eldragon on 2007-06-28
mild. theres something wrong with the rhythmbox backport....its nowhere near usable.

maybe its intentional since its a backport, and its noway expected to be usable. just letting know in case its not supposed to be in your repo if it has mayor bugs.

i managed to get the feisty official version disabling your repo after installing what i needed (pidgin and tbird2).

do you know how to ban certain packages from your repo instead of disabling it? appreciate the work you've done.

cheers.

---

### Post by mlind on 2007-06-28
> **eldragon said:**
> mild. theres something wrong with the rhythmbox backport....its nowhere near usable.

maybe its intentional since its a backport, and its noway expected to be usable. just letting know in case its not supposed to be in your repo if it has mayor bugs.

i managed to get the feisty official version disabling your repo after installing what i needed (pidgin and tbird2).

do you know how to ban certain packages from your repo instead of disabling it? appreciate the work you've done.

cheers.

yes, the 0.11 was very unstable for me too. I should probably upload recently released 0.11.1, works much better. You can use apt pinning to lock down specific packages, so those won't get upgraded. Easiest way is to probably use synaptic for this.

---

### Post by DoomedTX on 2007-07-01
mlind, after upgrading to TB 2.0.0.4 from your repo I've lost nearly all the certificate authorities from the "Authorities" tab. I have the 1/2 dozen or so that I manually added, but not the default CAs. I'm guessing this has to do with the "mozilla-thunderbird" to "thunderbird" name change, but I'm not sure which file holds the default list of CAs. Any ideas?

---

### Post by mlind on 2007-07-01
> **DoomedTX said:**
> mlind, after upgrading to TB 2.0.0.4 from your repo I've lost nearly all the certificate authorities from the "Authorities" tab. I have the 1/2 dozen or so that I manually added, but not the default CAs. I'm guessing this has to do with the "mozilla-thunderbird" to "thunderbird" name change, but I'm not sure which file holds the default list of CAs. Any ideas?

hey thank you for noticing this. /usr/lib/thunderbird/libnssckbi.so is a broken symlink that should point to ../firefox/libnssckbi.so. I'll upload a fixed package right away.

You can fix this manually by doing
```

cd /usr/lib/thunderbird
sudo rm libnssckbi.so
sudo ln -s ../firefox/libnssckbi.so

```

---

### Post by tim71 on 2007-07-15
I added iuculano's repository some time ago and installed Thunderbird 2 from there. However a strange problem appeared - I could not update Thunderbird extensions any more. Just "An error occured when try to update xxx extension" messages. I thought that something may be wrong with my setup or Thunderbird profile, so I made a new profile for testing. Also I checked all the permissions for the profile's folder(s) and strangely some extensions got a read-only permissions for some files (444). Same problem also occured with a new profile.

After I added mlind's repository for some other reason I got also Thunderbird updated and this problem disappeared. 

So I cannot be absolutely 100% positively sure, but it seems, that at least 32bit binary for Thunderbird 2 in iuculano's reposirory has some kind of issue with this at the current moment.

---

### Post by BlackAnthrax on 2007-07-18
For those that do not understand installing the tar.gz from the Mozilla site, I've wrote a script to download it, extract it, copy it to the correct location (/etc/opt/), delete the "temporary files", and then create a menu entry. Instructions are here:
[http://techystuff.info/?p=64]("http://techystuff.info/?p=64")
The script is safe (Be careful when running random scripts off the web), however I would advise you to check the script out yourself if you don't trust it fully. 
[CENTER]:guitar:[/CENTER]

---

### Post by mike102282 on 2007-07-18
> **BlackAnthrax said:**
> For those that do not understand installing the tar.gz from the Mozilla site, I've wrote a script to download it, extract it, copy it to the correct location (/etc/opt/), delete the "temporary files", and then create a menu entry. Instructions are here:
[http://techystuff.info/?p=64]("http://techystuff.info/?p=64")
The script is safe (Be careful when running random scripts off the web), however I would advise you to check the script out yourself if you don't trust it fully. 
[CENTER]:guitar:[/CENTER]

cool thanks

---

### Post by nanotube on 2007-07-24
> **BlackAnthrax said:**
> For those that do not understand installing the tar.gz from the Mozilla site, I've wrote a script to download it, extract it, copy it to the correct location (/etc/opt/), delete the "temporary files", and then create a menu entry. Instructions are here:
[http://techystuff.info/?p=64]("http://techystuff.info/?p=64")
The script is safe (Be careful when running random scripts off the web), however I would advise you to check the script out yourself if you don't trust it fully. 
[CENTER]:guitar:[/CENTER]

ehrm... nice work, but... check out the already-existing ubuntuzilla project (see link in my sig). :)

---

