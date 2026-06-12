---
title: "ClamAV and Clamtk on Ubuntu 7.10 x64"
date: 2008-02-22
forum: Security Discussions
---

### Post by Kivech on 2008-02-22
Ok, installing both of them is easy through the Synaptic Package Manager. I'm running into a problem though.

Clamtk is claiming that there are no signature files, while obviously there are. I managed to find out the difference: Clamtk is looking for them in /etc while they are in /etc/clamav.

Edit: not sure about the paths btw, but for sure they don't correspond. 

So all I need to know is where I can change the path where Clamtk expects/updates the signature files and I'm set.

Does anyone know? Or is this a hard coded path?

Kivech

---

### Post by Kivech on 2008-02-22
Thinking over my problem and having checked both the ClamAV and Clamtk sites, I got a daring idea...

Mind you, I'm still quite fresh with this Linux stuff. :p

So if I download the latest releases of both programs and install them, would I go about do it like this for each program?

1) Untar the files somewhere in my /home dir (for potential later use)
2) Go to the terminal and do: 

make
sudo make install

And that would be it? Or am I seeing things too simple now?
Ah, and what about getting automatic updates, what would I have to add to my resources.list to get them updated automatically?

Unless there is a simple way of getting things to work with the Synaptic PM of course, that way I'd know the guys at Ubuntu verified it all first.

Kivech

---

### Post by Kivech on 2008-02-25
So no one managed to get Clamtk working properly?

---

### Post by drdos2006 on 2008-03-17
Clamtk requires root access to update the signatures.

From a terminal, run :-  sudo clamtk
Type in your password:- ******
Go to Help and select Update Signatures.

regards

---

### Post by the_phenom on 2008-03-17
That's an old version in the repositories - download the latest one here:

[http://packages.ubuntu.com/hardy/all/clamtk/download]("http://packages.ubuntu.com/hardy/all/clamtk/download")

---

