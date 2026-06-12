---
title: "can some one explain what a repository is?"
date: 2005-10-16
forum: Repositories &amp; Backports
---

### Post by onesojourner on 2005-10-16
Hello I am new here. I did a quick search and didn't ever find a thread that actually gives me a quick idea of what a repository is and how it works. I'm sure this has been covered many times so sorry about the repeat post. the back ports has a sticky that explains that. is there a thread like that for this forum?

---

### Post by arctic on 2005-10-16
A repository is a collection of software for a linux distribution on a server. You grab information on the software that is available on the server using the packaging tools (in ubuntu it is apt-get) and download the software directly from those servers. As there are many folders in the web, they need to be kept separate. Ubuntu 5.10 will have different repositories than Ubuntu 5.04 or Mandriva or Redhat or Debian distros. Keeping the repositories split from each other ensures that your system will stay safe and not break due to incompatible software.

---

### Post by David Haas on 2005-10-16
onesojourner--You can read about repositories in Synaptic Package Manager.
Go to System>Administration>Synaptic Package Manager, and then 
in Synaptic, click Help>Contents>Repositories to read about Repositories.
They are organized, you'll see, into Main, Restricted, Universe, and Multiverse. You'll want to be clear about what these refer to.
Enjoy Ubuntu,
David

---

