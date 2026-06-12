---
title: "Security &amp; Privacy"
date: 2009-12-09
forum: Ubuntu One (CLOSED)
---

### Post by damnick on 2009-12-09
I would like to know the Security & Privacy options of ubuntu one against to dropbox

From the dropbox site:

**1.** Shared folders are viewable only by people you invite.
**2.** All transmission of file data and metadata occurs over an encrypted channel (SSL).
**3.** All files stored on Dropbox servers are encrypted (AES-256) and are inaccessible without your account password.
**4.** Dropbox website and client software have been hardened against attacks from hackers.
**5.** Dropbox employees are not able to view any user's files.
**6.** Online access to your files requires your username and password.
**7.** Public files are only viewable by people who have a link to the file(s). Public folders are not browsable or searchable.

So ubuntu one is more secure from dropbox or not?

---

### Post by manoriax on 2009-12-09
I guess it is not. Files are not saved encrypted as far as I know, thank's one big contra.

---

### Post by ruffus910 on 2009-12-11
I too, am quite worried about security. While I have no personal information on any computer (why would I? its asking for trouble) nor would I upload any sensitive data to this service, Im still a bit paranoid. Ive had the feds breathing down my back once before (for an unrelated matter), so I am a little stressed about security and privacy. Anyone who could address my fears would be helpful.

Thank you.

---

### Post by craig.o on 2009-12-14
> **manoriax said:**
> I guess it is not. Files are not saved encrypted as far as I know, thank's one big contra.

Files are definitely not encrypted.  U1's security policy page: [https://wiki.ubuntu.com/UbuntuOne/Security]("https://wiki.ubuntu.com/UbuntuOne/Security")

Another dropbox-like service which does use encryption is SpiderOak: [https://spideroak.com/]("https://spideroak.com/")

hope that helps,
-Craig

---

### Post by Jimmyfj on 2009-12-16
Really. I fail to see what the problem is here? Canonical has to comply with different laws in different countries. Thus they have to have the data available if the authorities demands a copy, but hey - how hard is it to work around that? RAR-files are easy to create with a password for decompressing the content. Then again if you really HAVE something to hide, the Internet would be a poor choice of media.

---

### Post by stuartlangridge on 2009-12-18
> **craig.o said:**
> Files are definitely not encrypted.  U1's security policy page: [https://wiki.ubuntu.com/UbuntuOne/Security]("https://wiki.ubuntu.com/UbuntuOne/Security")

The intention is that Ubuntu One integrates with the existing encryption software in Ubuntu, rather than doing something custom on the server. manosx has been working on integrating Ubuntu's Encrypted Private Folders with Ubuntu One, and there's some notes on how to do that so you store encrypted data in Ubuntu One at [http://ubuntuforums.org/showthread.php?p=8517221](http://ubuntuforums.org/showthread.php?p=8517221), which looks really cool. (Remember that if you encrypt files in Ubuntu One you won't be able to share them with anybody, though.)

---

