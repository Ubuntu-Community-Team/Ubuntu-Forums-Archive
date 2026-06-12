---
title: "Dropbox"
date: 2011-11-30
forum: The Cafe
---

### Post by dRounse on 2011-11-30
So here is a thought...
What if you could configure Dropbox to be a server or something like that for all your files on your computer? Now this question needs to be explained more... I mean what if you could use the standard 2GB of free space, and just make it so when you are on Dropbox on something else like a laptop you can access your whole hard drive on your desktop. I know this would just be a server you could set up anyway, but right now I dont have money for a server, and I'm in the process of building a cheapo server out of an old Acer desktop. Sorry if this sounds like a stupid idea.

---

### Post by PhilGil on 2011-11-30
You mean like [this]("http://www.tonido.com/")? Or [this](http://sparkleshare.org/)?

---

### Post by Primefalcon on 2011-11-30
You could get a cheap godaddy shared account and ssh/sftp into it as needed

---

### Post by CryptAck on 2011-11-30
> **Primefalcon said:**
> You could get a cheap godaddy shared account and ssh/sftp into it as needed

Yup, and it works awesome! :)

---

### Post by forrestcupp on 2011-11-30
That would be awesome, but it wouldn't work with Dropbox. Dropbox clients are programmed to sync a directory with their own server. A similar program could be created, but if Dropbox clients are proprietary, there's no hope of changing it unless you could talk their devs into adding a feature like that. It would be cool if it could be that way, though. 

I could be wrong, but I think you'll have to have a static IP address to build a server that can be accessed from the internet outside of your home network.

---

### Post by BrokenKingpin on 2011-11-30
Could you not just take your old acer desktop and setup a Samaba share on it. Then any files you want to share to all your computers just put them in that share.

And if at that point you still want some files synced between all computers you could use Dropbox/Spideraok to sync two gigs of that share to all PCs.

---

### Post by dRounse on 2011-11-30
> **BrokenKingpin said:**
> Could you not just take your old acer desktop and setup a Samaba share on it. Then any files you want to share to all your computers just put them in that share.

And if at that point you still want some files synced between all computers you could use Dropbox/Spideraok to sync two gigs of that share to all PCs.

I could do that, I just wanted to come up up with something crazy like almost reconfiguring Dropbox

---

### Post by Copper Bezel on 2011-11-30
If you're looking for crazy things to do with Dropbox, try moving the configuration folder for a browser - or anything else - into your Dropbox, then symlinking back to it, from a pair of machines. = )

Edit: And possibly .local, if you just want to break something. = D

---

### Post by BrokenKingpin on 2011-12-02
> **dRounse said:**
> I could do that, I just wanted to come up up with something crazy like almost reconfiguring Dropbox
Try writing your own sync scripts using rsync if you just want to tinker. If you just want a solution that is simple and works, Samba share all the way. Before trying anything too crazy backup your data, or you might just end up losing it.

---

### Post by KingYaba on 2011-12-02
I stopped using Dropbox when Ubuntu One came out.

---

### Post by ikt on 2011-12-02
> **KingYaba said:**
> I stopped using Dropbox when Ubuntu One came out.

I stopped using both when sparkleshare came out.

---

### Post by Plumtreed on 2011-12-02
You might get to where you want to go with 'owncloud'....easier to 'play' with!

---

