---
title: "Hacked!!"
date: 2006-11-06
forum: Server Platforms
---

### Post by kehan on 2006-11-06
Over the weekend I found my laptop humming away with CPU at 100% and this raised a little concern.

I then rooted around and fount that somebody had logged into my guest account via SSH and was running a port scanner and logging IP addresses etc into this account and making them available through an http server running under that account! - I was shocked but have to admit that I was silly giving the user account the ID of guest and also silly to open up the SSH port.

The guest account had a compressed file Dragonu.tgz within it and this contained several files including a perl script called pscan which was what seemed to be doing all of the work.

I have since deleted the account and closed SSH from outside my network as I don't need access from outside for the next few months.

Is there any point in tracking back to the ip address who had hacked me or would it have likely come through a whole series of other addresses and obscured itself. Also is there anywhere I could send the suspect files to so that others can be protected from them?

Also would clamAV and the likes have detected this port scanner being installed and running on my machine?

Sorry for the long post but just needed to vent my fustration.

Cheers,
Kehan

---

### Post by dogon on 2006-11-06
Keep your logs of the event and the files that this hacker left on your system. The reason is that if one of the scanned computers owners comes to you to object you can tell them you were hacked and have something to help them on their search.

I know at least one person who was able to avoid being banned from his ISP with those logs. Someone had used his computer to target a swiss bank and the swiss bank was slightly irritated by this.

Never open up what you dont really use :)

---

### Post by nocturn on 2006-11-06
Reinstall your system and use new passwords on every single account.

---

### Post by trash on 2006-11-06
> **nocturn said:**
> Reinstall your system and use new passwords on every single account.

Is a reinstall really needed if all the passwords are changed?

---

### Post by nocturn on 2006-11-06
> **trash said:**
> Is a reinstall really needed if all the passwords are changed?

Yes.  If your system has been compromised, you cannot trust anything on it, even your top/ps binaries may be hacked.

A complete reinstall is the only way to clean it up.

---

### Post by trash on 2006-11-06
good to know, thanks!

---

### Post by nocturn on 2006-11-06
> **nocturn said:**
> Yes.  If your system has been compromised, you cannot trust anything on it, even your top/ps binaries may be hacked.

A complete reinstall is the only way to clean it up.

Allow me to demonstrate something.  Generate an SSH key on another system.  Put the id_rsa.pub inside .ssh/authorized_keys on the orignal machine.  Change passwords

Log in from the second machine, you'll be logged in without supplying a password.  

This is just an example using standard installed components, I can have a custom program listening or checking a mailaccount that gives me access again, even after you change all the passwords.

---

### Post by nocturn on 2006-11-06
> **trash said:**
> good to know, thanks!

Good luck!

---

### Post by Mimsy on 2006-11-06
> **MJN said:**
> It might be worth putting your machine back into its box until you learn some fundamental security issues.
 
I'm often surprised how many attempted 'guest' account logins I see in my logs and wonder who on Earth would be so foolish as to leave one open...

No matter how right that may be, the OP is better helped by constructive suggestions.

Just a thought.

/Mimsy

---

### Post by kehan on 2006-11-06
the machine was originally intended to be completely behind a firewall then I had to access it from outside so had to open up ssh.

Anyway comments like 
'putting you pc back in the box before you learn some basic security ...'

are not the kind of behaviour I have learned to expect from the Ubuntu community - very disappointed in that!!!

Thanks to everybody _else_ for their constructive suggestions.

---

### Post by kehan on 2006-11-06
> **dogon said:**
> Keep your logs of the event and the files that this hacker left on your system.

have the syslog and auth log - any other standard logs worth looking out for?
Thanks,
Kehan

---

### Post by MJN on 2006-11-06
> **Mimsy said:**
> No matter how right that may be, the OP is better helped by constructive suggestions.
 
I thought it was constructive!
 
I was somewhat perplexed by the OP's evident knowledge on the consequences of a compromised machine yet (s)he still seemingly had a non/weak-passworded guest account open to all.
 
Thinking about it now, I'm wondering if this is a troll, in which case I've fallen for it hook line and sinker! ;)
 
Mathew

---

### Post by Mimsy on 2006-11-06
Question: How do I keep the machine from being hacked again?
Answer: Stop using it and rtfm!

Constructive? Not really.

Alternatively, maybe you didn't mean your answer to sound like that, and I misunderstood you.

/Mimsy

---

### Post by MJN on 2006-11-06
I hear what you're saying and I'm sorry, particularly to Kohen, if it caused offence.
 
However, to be fair, the OP wasn't asking how not to get hacked again - they already knew that... indeed it is clear from the original post that a weak guest account was known to be an achiles heal yet still was allowed to exist.
 
Unfortunately no amount of RTFM can stop knowingly exposing an exploitable server hence the advice to box it up!
 
Remember, the victim is not just the OP's server, it's everyone else that suffers as a result of spambots and God-knows-what-else that gets dumped on these machines!
 
Mathew

---

### Post by Mimsy on 2006-11-06
True enough; computers are only as secure as the users make them. (Though to be fair, rtfm isn't really that good an answer, mainly because the f-manual rarely is as helpful as it ought to be.) But since we seem to be in full agreement on that, I'm going to drop this subject now. I misunderstood your post, and that's the end of it.

/Mimsy

---

### Post by Macchi on 2006-11-06
For improved security of SSH servers on the internet you can use DenyHosts. This tool updates continuously a list of attackers and feeds them into the /etc/hosts.deny. The ssh server can thus refuse all connections to known attackers and blocks dynamically any brute force attempts to break in. Furthermore, after a number of unauthorized login attempts the attacker can be reported to a global blacklist.  
 
DenyHosts doesn't eliminate all security threats but definitely helps a lot!

---

