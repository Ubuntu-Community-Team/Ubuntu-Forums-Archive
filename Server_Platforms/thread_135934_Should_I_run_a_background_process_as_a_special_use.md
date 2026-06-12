---
title: "Should I run a background process as a special user or root?"
date: 2006-02-24
forum: Server Platforms
---

### Post by jpkotta on 2006-02-24
I run Folding@Home.  I think it's secure enough, I know of no vulnerabilities.  It only connects to Folding@Home servers, and only allows Folding@Home servers to connect to it.  

However, I ran Gentoo for a while, and noticed that the Folding@Home ebuild created a foldingathome user that was basically restricted to running Folding@Home and nothing else.  Also, the part that connects to the servers is closed source, to make sure no one tampers with it and generates bogus results.

I'm making an F@H installer for Ubuntu.  Should I have it create a new user, or is this overly paranoid and a source of bugs and usability issues?

---

### Post by nanotube on 2006-02-27
i dont see how it would hurt to have a separate user for it. :)

---

### Post by imagine on 2006-02-27
If it doesn't require root privileges, don't run it as root. Simple rule : )

---

### Post by jpkotta on 2006-02-27
The only reason for not running as a separate user is that it adds an extra complication.  Like I said, I'm making an installer for others to use, and this would add an extra thing to go wrong.  And I'm lazy.

I'll probably end up making the user anyway.

---

### Post by LordHunter317 on 2006-02-27
If you're making this for other people, it's absolutely your burden to do it and do it correctly.  And the SETI client has had security issues in the past, so it had damn well run unprivileged.

---

