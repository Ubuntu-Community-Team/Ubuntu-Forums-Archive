---
title: "what happens with a faked repository"
date: 2012-11-10
forum: Security
---

### Post by jsvidyad on 2012-11-10
Hello,

   My question is about a certain scenario: Say I have connected to an unknown wireless or wired network using my ubuntu laptop. The DNS server ip addresses for this network have been set(by the owner of the network or by a malicious hacker) to point to a fake, malicious DNS server set up by that person. Now, I try to update my ubuntu system using the commands
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get dselect-upgrade

Now, the fake DNS server directs one of the repositories(say us.archive.ubuntu.com or packages.medibuntu.org or some other repo) to a false, malicious ip address set up by that person where he has set up a fake, malicious repository. The upgrade process reports to me that there are software upgrades(updates) for my ubuntu system and I give my assent to install those upgrades(updates). So, the fake, malicious upgrades(updates) are installed on my ubuntu system and the malicious guy/hacker has managed to install malware/spyware/viruses on my ubuntu system. Is such a scenario possible?

---

### Post by SeijiSensei on 2012-11-10
Yes, it's possible but highly unlikely.

If you're worried about this, pick a different repository server.  I use one located at a nearby university.  There are hundreds of options.

---

### Post by cwsnyder on 2012-11-10
Said malicious hacker would have to not just control the DNS, the repository would also have to fake the 'signatures' of the repositories and packages, which I believe have an AES two-part encryption.

---

### Post by SeijiSensei on 2012-11-10
You're right.  I forgot entirely about package signing.  I believe an effective compromise would require gaining access to Canonical's private key that is used to sign the packages.  There was an event like this in 2008 when someone [breached Fedora's signing server]("http://www.theregister.co.uk/2011/01/25/fedora_server_compromised/").  While RedHat didn't believe the passphrase was compromised, they judiciously changed it anyway.

---

### Post by Hungry Man on 2012-11-10
PGP would prevent this. They would need the private keys from the repository to sign their payloads, otherwise they'd send it over and the update would fail.

Of course, certificates get stolen all the time, which is why I've said before that updates should be handled over HTTPS to prevent MITM attacks where the signatures have been stolen.

---

### Post by cwsnyder on 2012-11-10
@Hungry Man: I'm not sure how you would set up for an https:// connection to a local repository on a LAN.  SSH, yes, but for https:// you would almost have to have a web server.

---

### Post by Hungry Man on 2012-11-10
Right now updates are handled through HTTP. All of the repos on the list are HTTP sites.

---

### Post by rookcifer on 2012-11-10
> **SeijiSensei said:**
> Yes, it's possible but highly unlikely.

No, it's not possible.  The attacker would not have Ubuntu's repository signing key and the "update" would fail.

---

### Post by cwsnyder on 2012-11-10
> **Hungry Man said:**
> Right now updates are handled through HTTP. All of the repos on the list are HTTP sites.Actually that isn't quite correct.  Some mirrors are ftp sites for both downloads and updates.

---

### Post by jsvidyad on 2012-11-10
Hello,

  From what I understand, you are saying that the scenario I mentioned won't happen because the fake packages won't have the correct signatures, right? If the signatures don't match, what happens? Does apt give me a warning or something? Or does it give an error message and exit?

---

### Post by jerome1232 on 2012-11-10
I know apt-get gives you a warning and asks if you'd like to install anyways. I don't think I've ever seen it happen in update manager, but I am fairly certain (85% sure) it refuses to do it and tells you to fix the problem.

---

### Post by jsvidyad on 2012-11-10
> I know apt-get gives you a warning and asks if you'd like to install anyways. 

So, what you are saying is that apt will give a warning if the signatures of the malicious upgrades(updates) from the fake repository don't match the signatures on the packages in the genuine repository? Are you sure about that? Sorry, I am a little worried about this. that's why I'm asking this question.

What happens if the malicious upgrades(updates) from the fake repository **_do not_** have any signature? In this case, will apt-get still give a warning or will it just perform the update(upgrade) with no warning at all and install those malicious upgrades(updates)?

---

### Post by jerome1232 on 2012-11-10
snip

On my computer now, no signature is the same as a bad one.

Read up about it here: [https://help.ubuntu.com/community/SecureApt](https://help.ubuntu.com/community/SecureApt)

This is what apt-get update looks like when you see the error
```

W: GPG error: http://ftp.us.debian.org testing Release: The following signatures  couldn't be verified because the public key is not available: NO_PUBKEY 010908312D230C5F
```

This is what apt-get upgrade looks like

```

WARNING: The following packages cannot be authenticated!   libglib-perl libgtk2-perl Install these packages without verification [y/N]?
```

---

### Post by Ms. Daisy on 2012-11-10
Based on my experience when I hadn't gotten the pgp keys for some repositories, the Update Manager will simply fail to install the unsigned updates by default. On the command line you're given the option to allow them to install anyway, but it gives you a pretty clear warning.

---

### Post by jsvidyad on 2012-11-10
Hello, It is still not clear to me what happens when the faked repository tries to give malicious updates(upgrades) to my computer and those updates(upgrades) have **_no signature_**. In this case, will apt-get give the same warning it gives when it finds malicious updates(upgrades) which have a signature different from the signatures on packages in the genuine repository?

---

### Post by jerome1232 on 2012-11-11
Yes, no signature is the same as a bad signature as far as apt-get is concerned.

That's actually usually the situation that arises because either the developer forgot to sign his packages or someone added a ppa and forgot to add the public key so apt-get can check the packages.

---

### Post by jsvidyad on 2012-11-11
Thank You all for your help. Cheers!!!!


Actually, just one more thing. From the posts in this thread, what I understand is that I can't end up installing malicious updates(upgrades) from a fake repository(for example in the scenario I mentioned in my first post) without apt-get issuing me warnings. Is that right?

---

### Post by jsvidyad on 2012-11-11
Sorry. Just hoping someone would reply.

---

### Post by jsvidyad on 2012-11-11
Can someone please help me here.

---

### Post by jerome1232 on 2012-11-11
Wait at least 24 hours before bumping your own thread, it's considered rude to bump it so quickly, could you imagine what this forum would be like if everybody did that?


Yes, apt-get checks packages to make sure they are signed by the private key, so long as the private key is kept just that, private, you can be sure it's the correct package from the person you expect it from.

---

### Post by OpSecShellshock on 2012-11-11
Correct, you won't get malicious, unsigned packages to install without being warned first. But moving a level up (or down if you're really nerdy) when folks advise against doing anything sensitive or critical on a network outside your own control, I would think package management or software installation would be considered one of those things anyway.

---

### Post by kurt18947 on 2012-11-11
I did what SeijiSensei recommended.  I changed my repository to a university nearby though mainly to reduce the load on Ubuntu's servers and data pipes.  It sure seems like there are quite a few safeguards to circumvent or defeat to be able to create a functional fake repository.

---

### Post by cwsnyder on 2012-11-11
Functional & fake repository still would depend on user _not paying attention_.  That is one of the major differences between Windows and Linux.  The only exploits which got through Linux's basic controls are those which use social engineering and get by, usually, new users only.

---

