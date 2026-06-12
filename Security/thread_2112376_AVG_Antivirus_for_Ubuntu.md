---
title: "AVG Antivirus for Ubuntu"
date: 2013-02-04
forum: Security
---

### Post by latvian on 2013-02-04
Hello everyone,

I have been reading about viruses in Linux and I am not really sure if this is something to worry about or not. Anyway, I have installed AVG antivirus on Ubuntu and I got the following output

```
Files scanned     :  0(0)
Infections found  :  0(0)
PUPs found        :  0
Files healed      :  0
Warnings reported :  0
Errors reported   :  1

```

My question is: how to know which file has been infected?

---

### Post by Cheesemill on 2013-02-04
> **latvian said:**
> Hello everyone,

I have been reading about viruses in Linux and I am not really sure if this is something to worry about or not. Anyway, I have installed AVG antivirus on Ubuntu and I got the following output

```
Files scanned     :  0(0)
[COLOR=Red]** Infections found  :  0(0)**[/COLOR]
PUPs found        :  0
Files healed      :  0
Warnings reported :  0
Errors reported   :  1

```My question is: how to know which file has been infected?
No files have been infected.

You could look in the AVG logs to see what the error was.

---

### Post by Frogs Hair on 2013-02-04
You also scanned no files either. ```
Files scanned     :  0(0)
```

---

### Post by Impavidus on 2013-02-04
It appears there was some error preventing the scan from starting.

BTW, I wouldn't worry too much about viruses. Most Linux users don't use a virus scanner, except when they share a lot of files with windows (and that only to protect windows).

---

### Post by takuie on 2013-02-04
Virus on Linux?  Is it even possible?

---

### Post by dcstar on 2013-02-05
> **takuie said:**
> Virus on Linux?  Is it even possible?

I have never seen one credible post about a Linux virus in these forums in the time I have been on them since 2005.

The only posts on the subject seem to be from panicky Windows users who don't understand that 99.9% of all the rubbish in the media about all malware **only** applies to that platform.

The biggest security issue in Linux are stupid users using insecure third-party repositories and installing software that has no guarantee of what it does or where it actually comes from.

---

### Post by 3rdalbum on 2013-02-05
I was going to write an analogy of "Why would you treat a steel fence for termites" but if a little knowledge is dangerous, maybe a lot of knowledge will be beneficial.

The facts regarding Linux viruses are:

1. Although the Wikipedia page lists about 40 viruses which have appeared on Linux at some point in time, none of them are in the wild and none of them would even work on a modern Linux system.

2. You may be thinking "forty viruses in 22 years of Linux - that's nearly two per year". Let's compare that to an estimated 10,000 pieces of Windows malware **per year**.

3. Most of those forty Linux viruses came about in Linux's early days; I can only remember two Linux "viruses" from 2005 onwards. In other words, the rate of virus writing for Linux has slowed dramatically.

3. Only a tiny, teeny, miniscule percentage of Linux users have ever seen a Linux virus. It must be less than 1%.

4. The last Linux "virus" was actually a trojan horse. It infected maybe a couple of hundred people. Maybe up to a thousand.

5. The website that inadvertently hosted the trojan (which you had to download and install as root) removed the trojan within a couple of days. No further infections occurred - the trojan was not self-replicating.

6. Within a week, the payload was removed from the author's website, rendering the trojan entirely useless even for existing infections or new infections (had there been any).

7. As far as I'm aware, the only anti-virus program that can detect the trojan is ClamAV - the other vendors like AVG didn't even bother.

8. Although Linux is a high-value target for malware (financial systems worldwide run mostly on Linux), it's very difficult to write a decent piece of malware for Linux due to its ever-increasing level of security.

So there you have it - your AVG is useless for picking up Linux viruses. There's just nothing for it to find anywhere, and even when anyone manages to write a virus it never spreads to more than a handful of Linux users.

---

### Post by codemaniac on 2013-02-05
Thread moved to "Security Discussions".

---

### Post by conquerorodueko on 2013-02-06
TAKUIE

Is linux prone to viruses? - Virus on Linux? Is it even possible?  YES, ABSOLUTELY
Do you need an antivirus? NOT REALLY

LATVIAN AND TAKUIE
Here it is.

Who understands the ubuntu codes better and faster than the original programmers themselves? 
THINK OF IT AS THE PROGRAMMERS RACING AGAINST THEIR ADVERSARY.

There are perhaps hundreds of programmers working together,merging their codes and there is a handful of malicious virus writers working individually with the time on their hands. The result, the updates come out quicker than the virus can be written.

Viruses are written to exploit and take advantage of security gaps missed by the programmers while they focused on functionality [getting it to work and be compatible for wider range of use]. In essence, by the time the virus is completed and released, the update has already patched it rendering the virus useless.

The only reason to really use an antivirus is if the programmers stop reviewing their codes and releasing the updates. Even an antivirus company cannot understand the codes faster than the programmers otherwise the antivirus company can write the viruses themselves, release the virus then make money from selling you the antivirus.

IF UBUNTU BECOMES WIDELY EXPLOITED BY VIRUSES IT CAN ONLY MEAN ONE OF TWO THINGS:
1.) THE PROGRAMMERS HAVE STOPPED/SLOWED DOWN REVIEWING THEIR CODES AND RELEASING THE PATCHES
2.) THE PROGRAMMERS THEMSELVES ARE WRITING THE VIRUS [they will have to look internally for the devious one amongst them]

---

### Post by Adam_GUI on 2013-02-06
I've used my system for file backup a couple of times.  Especially if I've had to make backups from an infected machine.
Antivirus on my linux box isn't so much about having my machine execute the code as it is finding infected code on another OS.

Every so often, ClamAV or Avast has found a trojan or virus hidden in an archived tmp folder from another user's Internet Explorer cache.
Well, ClamAV anyway.  Avast has errored out since somewhere around 11.10.

Clamtk will list problem files in View > Manage Histories and in Quarantine > Status/Maintenance.  
I don't remember Clam allowing me to clean a file, so much as giving me the file name and location and just letting me delete it outright.

Either way, it's more about keeping files clean for others than executing code on my own machine.

---

