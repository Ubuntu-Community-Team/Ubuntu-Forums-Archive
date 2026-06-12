---
title: "pwd protect a server directory containing a website"
date: 2011-07-08
forum: Server Platforms
---

### Post by mzycdth on 2011-07-08
Hi everyone,

My brother and I currently use a shared server, we both connect via SSH. I store files (via SFTP) on it as I only normally use a laptop. He uses to host his own personal files and also a public website promoting his photography business.

I am interested in cryptography and security and have restricted our SSH connections to require keys and use encfs to encrypt my personal folder. Comments on this are welcome.

I am struggling to work out how to protect his home folder without preventing access to his site. Normal methods prevent access entirely or require the web browser to enter a password (no good for promotion). I would like to prevent both alien users and myself from accessing his home folder but still allow his website to be functional from within this area of restricted access. Both the site and his personal files need to be protected.

Is this possible? Thanks for any help.

---

### Post by rubylaser on 2011-07-08
A website is public anyways, so why not put the website in a public folder like /var/www and then encrypt his home directory like yours.  This seems like a case of making something harder than it needs to be.

---

### Post by mzycdth on 2011-07-08
I suspect you're probably right! I'll run that solution past him.

With regards to server side encryption of an existing directory tree (rather than a single folder) are there any obvious tools?

Thank you for the help

---

