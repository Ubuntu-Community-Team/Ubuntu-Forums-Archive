---
title: "Tiger John Chkrootkit"
date: 2011-12-30
forum: Security
---

### Post by 0011235813 on 2011-12-30
Hi everyone! I recently installed a program called Tiger John Chkrootkit: *sudo apt-get install tiger john chkrootkit* [in a terminal, Ctr+Alt+T] Then, I ran the software. I then got a message telling me that the HTML document was located somewhere in /var/log (I can't remember exactly where it was). The funny thing is, I can't open the folder where it's located! Apparently, I do not have the necessary permissions. I assume these folders require root privileges to access. Now, since Ubuntu Forums have made it clear I'm not supposed to login as root EVER... I'm a bit stuck on how to open the darn thing! I've tried: *gksudo firefox [EnterFileName]* but it works diddysquat. Does anyone know how to open the folder? Or do I need to log in as root?

---

### Post by MG&amp;TL on 2011-12-30
Well, either:

```
gksu nautilus
```

nautilus as root.

or one of:

```
sudo bash
```

```
sudo -i
```

```
sudo gnome-terminal
```

shell as root.

then navigate to where you want to be. Although changing directory to where you should be shouldn't be a problem.

NOTE: logging as root is entirely different, I understand. This is just launching something as root, which is perfectly possible whenever you run "sudo cp " or whatever. It's only temporary for one application.

---

### Post by Dangertux on 2011-12-30
Also if I recall Tiger generates files with spaces in them, if it does you'll need to double quote the file name.

---

### Post by MG&amp;TL on 2011-12-30
Like this:

```
cd "my dir"
```

or escape the space, like this:

```
cd my\ other\ dir
```

---

### Post by 0011235813 on 2011-12-30
> **MG&TL said:**
> Well, either:

```
gksu nautilus
```nautilus as root.

or one of:

```
sudo bash
``````
sudo -i
``````
sudo gnome-terminal
```shell as root.

then navigate to where you want to be. Although changing directory to where you should be shouldn't be a problem.

NOTE: logging as root is entirely different, I understand. This is just launching something as root, which is perfectly possible whenever you run &quot;sudo cp &quot; or whatever. It's only temporary for one application.

Thank you, ```
gksu nautilus
``` seems to have worked, and I was able to access the document. I am now confronted with a different headache however; what do with it? I have attached the document in this post, and if you(or anyone else reading this) could please take a little time to read through it, it would be much appreciated. PS: For everyone else who posted, I apologize for not trying out your solutions as well, you have to understand that I'm a bit lazy (by programmer standards anyway) and that I just read the first thing that came up. But thank you for the replies anyway.

---

### Post by MG&amp;TL on 2011-12-30
Can you give us a link to where you got it from?

---

### Post by 0011235813 on 2011-12-30
> **MG&TL said:**
> Can you give us a link to where you got it from?

I'm sorry, I'm not sure what you mean. Got what from? The chkrootkit? The document? I'm really not trying to be annoying here, but can you please be a little more specific?

---

### Post by Dangertux on 2011-12-30
That document is basically saying you have Ubuntu.

Ubuntu notoriously does terrible on security scans like that. It's laid out very differently then more standard implementations like CentOS or Fedora. There is nothing alarming in that document. If yuo have a question about a specific line feel free to post and I'll explain it.

---

### Post by MG&amp;TL on 2011-12-30
> **0011235813 said:**
> I'm sorry, I'm not sure what you mean. Got what from? The chkrootkit? The document? I'm really not trying to be annoying here, but can you please be a little more specific?

Sorry, I meant the chrootkit. My bad, but dangertux has it covered, anyway. Over to you, dangertux. ;)

---

### Post by 0011235813 on 2011-12-30
> **Dangertux said:**
> That document is basically saying you have Ubuntu.

Ubuntu notoriously does terrible on security scans like that. It's laid out very differently then more standard implementations like CentOS or Fedora. There is nothing alarming in that document. If yuo have a question about a specific line feel free to post and I'll explain it.

Ah well... Nice to now my computer is sound. Well I think we can close the thread now. Thanks for the help guys& girls!

---

### Post by Dangertux on 2011-12-30
Keep in mind that I said that there is nothing in THAT log that indicates compromise. For the same reason that false warnings are being spit out legitimate compromises may be being ignored. Food for thought.

---

### Post by 0011235813 on 2011-12-30
> **Dangertux said:**
> Keep in mind that I said that there is nothing in THAT log that indicates compromise. For the same reason that false warnings are being spit out legitimate compromises may be being ignored. Food for thought.

Interesting... I wonder, is there any chkrootkit out there that works better?  But thanks for looking through it, I'm not really an expert at this to be honest with you.

---

### Post by Dangertux on 2011-12-30
Open Source? No... Not really...

The reasoning being this -- Traditionally, most nix hacks are very targeted (minus silly SSH brute-forces and the like). That being said, payloads delivered are usually customized for a target, thus not easily signatured.

There really isn't much a "norm" of what to look for. Particularly in terms of Ubuntu since it is rather different than a typical Linux distro.

---

### Post by 0011235813 on 2011-12-31
> **Dangertux said:**
> Open Source? No... Not really...

The reasoning being this -- Traditionally, most nix hacks are very targeted (minus silly SSH brute-forces and the like). That being said, payloads delivered are usually customized for a target, thus not easily signatured.

There really isn't much a &quot;norm&quot; of what to look for. Particularly in terms of Ubuntu since it is rather different than a typical Linux distro.

Pity. Ah well, knowing how secure Ubuntu already is, and with all the modifications I've made, I'm not **THAT** concerned.

---

### Post by Dangertux on 2012-01-02
> **0011235813 said:**
> Pity. Ah well, knowing how secure Ubuntu already is, and with all the modifications I've made, I'm not **THAT** concerned.


I agree -- taking positive proactive security measures is much more productive than repeatedly scanning for something you won't likely find.

---

### Post by 0011235813 on 2012-01-03
> **Dangertux said:**
> I agree -- taking positive proactive security measures is much more productive than repeatedly scanning for something you won't likely find.

Let's see all I've done (tell me if you know any other measures) : 1.Firefox: Add-ons: NoScript Adblock Plus WOT FoxyProxy Spamavert BetterPrivacy BrowserProtect BugMeNot and if it makes any difference: FlashGot 2.Thunderbird: FoxyProxy basic No HTML  openPGP showIP 3.Sudo:using ```
sudo visudo
``` I changed sudo timeout to 0. 4.Firewall enabled 5.Password protected files (some of them) 6.Clamscan I think that's it... Oh, I forgot to mention IP shower for FF. (for example: It's telling me the site has an IP of: 91.189.94.12 and is located in the UK. The URL matches the domain name)

---

### Post by Dangertux on 2012-01-03
> **0011235813 said:**
> Let's see all I've done (tell me if you know any other measures) : 1.Firefox: Add-ons: NoScript Adblock Plus WOT FoxyProxy Spamavert BetterPrivacy BrowserProtect BugMeNot and if it makes any difference: FlashGot 2.Thunderbird: FoxyProxy basic No HTML  openPGP showIP 3.Sudo:using ```
sudo visudo
``` I changed sudo timeout to 0. 4.Firewall enabled 5.Password protected files (some of them) 6.Clamscan I think that's it... Oh, I forgot to mention IP shower for FF. (for example: It's telling me the site has an IP of: 91.189.94.12 and is located in the UK. The URL matches the domain name)

Apparmor profiles for commonly exploited applications? For instance media players , email clients and web browsers. This would be a good next step in my opinion. 

Also... Are you using strong passwords? A lot of people install a ton of security applications and configure a beastly firewall but roll around with a 6 character password. You'd be surprised ;-)

Hope this helps.

---

### Post by sammiev on 2012-01-03
> **0011235813 said:**
> Let's see all I've done (tell me if you know any other measures) : 1.Firefox: Add-ons: NoScript Adblock Plus WOT FoxyProxy Spamavert BetterPrivacy BrowserProtect BugMeNot and if it makes any difference: FlashGot 2.Thunderbird: FoxyProxy basic No HTML  openPGP showIP 3.Sudo:using ```
sudo visudo
``` I changed sudo timeout to 0. 4.Firewall enabled 5.Password protected files (some of them) 6.Clamscan I think that's it... Oh, I forgot to mention IP shower for FF. (for example: It's telling me the site has an IP of: 91.189.94.12 and is located in the UK. The URL matches the domain name)

The only thing missing is to unplug your computer and leave it off. ):P

How fast does your computer run? I thought I went to the extreme. Now with all that protection can it fail with one plugin fighting another:confused:

---

### Post by 0011235813 on 2012-01-04
> **Dangertux said:**
> Apparmor profiles for commonly exploited applications? For instance media players , email clients and web browsers. This would be a good next step in my opinion. 

Also... Are you using strong passwords? A lot of people install a ton of security applications and configure a beastly firewall but roll around with a 6 character password. You'd be surprised ;-)

Hope this helps.

I am using an 11 character password with capital letters and numbers. It rated "excellent" when I installed Ubuntu.  Do you know any profiles? I would be interested to hear where I can get them...

---

### Post by 0011235813 on 2012-01-04
> **sammiev said:**
> The only thing missing is to unplug your computer and leave it off. ):P

How fast does your computer run? I thought I went to the extreme. Now with all that protection can it fail with one plugin fighting another:confused:

LOL, I meant **usable** computer, but yeah, I get it.  I'm not sure what you mean "one plugin fighting each other", I only use one plugin to display each type of content (in fact, I've disabled some). Do you mean add-ons? They do make Firefox use more RAM, granted, but no serious draw in performance. It is funny though when I use ABP to block the adds on hide my @$$ proxy though.  Buy HMA premium now for $4.99 a month![/quote]  Open add-ons bar with Ctrl+/, select ABP, select hide an element, select the element, select 'apply element hiding rule" now there is no more add!

---

### Post by sammiev on 2012-01-04
I seen people with many virus checkers and usually one will fight the other and you have little to no protection. Got dizzy looking at your setup. LOL

---

### Post by 0011235813 on 2012-01-04
> **sammiev said:**
> I seen people with many virus checkers and usually one will fight the other and you have little to no protection. Got dizzy looking at your setup. LOL

I only have clamscan installed... But it's nice to know I'm not considered unprotected :)

---

