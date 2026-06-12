---
title: "Problem installing rkhunter"
date: 2011-01-02
forum: Security
---

### Post by PHANTOM X on 2011-01-02
[COLOR=black][FONT=Verdana]I have a friend I'm helping use/setup Ubuntu. He's having problems installing rkhunter. He downloaded the tar ball from the official website, but he's getting permission errors on installation.[/FONT][/COLOR]
 
 
 
[IMG]http://i898.photobucket.com/albums/ac185/Buttons88bucket/Screenshot-3.png[/IMG]

---

### Post by handy on 2011-01-02
Isn't it in the Ubuntu repo's?

If it is that will certainly be the best way to install it.

---

### Post by PHANTOM X on 2011-01-02
It is. But it's outdated. Latest is 1.3.8 the repos is 1.3.7

---

### Post by mail2345 on 2011-01-02
What commands did he use?

---

### Post by PHANTOM X on 2011-01-02
I am not sure. Have to get back to you on that. :)

---

### Post by PHANTOM X on 2011-01-02
These are the exact instructions I gave to him. I'm assuming he followed them exactly. Is it possible to find what has been inputed in the terminal via a log?
> Got some directions on Rkhunter now. [IMG]http://support2imdl.freeforums.org/images/smilies/icon_e_smile.gif[/IMG]
 
Download the archive from [here]("http://www.rootkit.nl/projects/rootkit_hunter.html") and save it to the desktop.
 
Once done right click and select extract here.
 
Navigate to the folder by typing the following in a terminal:
 
**Code:**
cd Desktop/rkhunter-1.3.8
 
 
Install by typing:
 
**Code:**
./installer.sh --install

---

### Post by bodhi.zazen on 2011-01-02
> **PHANTOM X said:**
> These are the exact instructions I gave to him. I'm assuming he followed them exactly. Is it possible to find what has been inputed in the terminal via a log?

You forgot, to install applications you almost certainly need to use sudo.

Perhaps if you ran the installer as root.

As you are installing outside of the repos, do not forget the instructions on how to check and install updates =)

---

### Post by PHANTOM X on 2011-01-02
Looks like that is the problem. Can't believe I missed that.#-o

---

### Post by HermanAB on 2011-01-02
Hmm, just as well that you are having trouble - it is a waste of time anyway...

---

### Post by handy on 2011-01-03
> **PHANTOM X said:**
> It is. But it's outdated. Latest is 1.3.8 the repos is 1.3.7

I use Arch so I didn't know that.

---

