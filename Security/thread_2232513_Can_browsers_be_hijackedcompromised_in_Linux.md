---
title: "Can browsers be hijacked/compromised in Linux"
date: 2014-07-02
forum: Security
---

### Post by Odyssey1942 on 2014-07-02
I understand that Linux is normally more secure than say Windows. I am wondering if the ease of installing extensions in Firefox, Chrome and Chromium compromises the otherwise strong security of Linux? 

Cannot remember whether, when I installed Script Defender, I had to do an administrative approval, but if not that would seem to be much less secure.

---

### Post by ian-weisser on 2014-07-02
It's not about ease of installation.
It's about the trust relationship between you and the software (extension) provider.

Do you trust Mozilla, for example, to ensure that it keeps malware-laden extensions out of it's respository of extensions?

Ease of installation only compromises your system if you (foolishly) install untrusted code from untrusted sites in the shadier parts of the internet, or permit your system to install untrusted code without any supervision. The former is a human fault, the latter is a system design fault...but one that was long ago forseen and prevented.

---

### Post by Odyssey1942 on 2014-07-02
Yours is a well considered comment, but I am unsure if it is so simple.

For example if I went to the New York Times website, that is something I would normally trust. If I remember correctly, it did once happen that a NYT page was compromised and had a poison pixel on it that ran malicious code. Thousands of Windows users were infected. I think there are other similar examples.

Were Linux users? I don't know the answer, but I assume not-at least not if they had to give admin approval and did not so approve.

But that is the question that I am asking. Can a browser be compromised in Ubuntu without admin approval being requested or given?

If not, why is there an extension called Script Defender?

Thanks for helping me understand this better.

---

### Post by ian-weisser on 2014-07-02
> **Odyssey1942 said:**
> For example if I went to the New York Times website, that is something I would normally trust. If I remember correctly, it did once happen that a NYT page was compromised and had a poison pixel on it that ran malicious code. Thousands of Windows users were infected. [...]

Were Linux users? [...]

Is it *theoretically* possible for a browser to be compromised by a website into running arbitrary code? Yes. Browsers are enormous pieces of software and may be vulnerable to any number of potential exploits.
But it's not easy. And developers patch such vulnerabilities very quickly once discovered...a poison pixel won't work anymore. And Ubuntu pushes out patched versions (security updates) quickly.

Have such explots *actually* compromised Linux systems? Not many. The market seems to be in Windows and Mac machines today. That could change.

What can you do to protect yourself? Well, the same things you do to protect from many other kinds of damage. Know your system. Automatic security updates. Regular backups. Encrypt sensitive files.

---

### Post by HermanAB on 2014-07-03
Yes, a browser can be compromised and that is why you should install App Armor or SELinux, because that will prevent the contagion from spreading to the rest of your system.

---

### Post by SeijiSensei on 2014-07-03
> **Odyssey1942 said:**
> For example if I went to the New York Times website, that is something I would normally trust. If I remember correctly, it did once happen that a NYT page was compromised and had a poison pixel on it that ran malicious code. Thousands of Windows users were infected. I think there are other similar examples.

Yes, I encountered that [compromise]("http://countermeasures.trendmicro.eu/new-york-times-pushes-fake-av-malvertisement/") on the Times's site, though it happened back in 2009.  It was delivered via a malicious Javascript included with an ad distributed through one of the paper's advertising channels.  It ran the "Antivirus 2010" scam.  When you closed your browser, the script detected the event and opened a window that purported to show your computer being scanned for viruses and discovering many, many culprits.  Marks were directed to purchase a bogus antivirus tool which would "fix" this problem.

Still, as a Linux user, I knew right away this was a hoax.  The "scanner" identified many infected .dll files on the "C: drive" of my machine.  Of course most Linux machines have no C: drive and no DLL files whatsoever.  So the moral of the story is to be vigilant and thoughtful.

---

### Post by Odyssey1942 on 2014-07-03
All, very helpful. Thanks.

Herman's comment got me to thinking. My gmail accounts are unbelievably slow to open, send, etc. in both Chrome and Chromium. I have asked about it in the Beginner forum, but not getting much assistance.

Could this be indicative of a compromised browser?

If so, how does one test?

---

### Post by HermanAB on 2014-07-04
You can use netstat and tcpdump to investigate what is going over the wire between you and a web site and its advertiser network.

---

### Post by bashiergui on 2014-07-05
I would also run a speed test. See if your download / upload speeds are dipping lower than you expect overall.

---

### Post by Gyokuro on 2014-07-05
Maybe for interested people but every year there is Pwn2Own ([https://en.wikipedia.org/wiki/Pwn2own](https://en.wikipedia.org/wiki/Pwn2own)) so yes it's possible and also check the browser changelogs and in case of chromium you can get famous in case you find a security hole: [http://www.chromium.org/Home/chromium-security/hall-of-fame](http://www.chromium.org/Home/chromium-security/hall-of-fame)

---

### Post by open2reason on 2014-07-06
Social engineering exploits and browsers that can be compromised when taken together can and do cause problems for people surfing the net. Patches that fix browser code deficiencies are imho easy to implement with automatic updates and such, but attacks using social engineering methods are  harder to thwart as you are dealing with the mind of a person and not a line of code with phishing and spearphishing being but two examples.

---

