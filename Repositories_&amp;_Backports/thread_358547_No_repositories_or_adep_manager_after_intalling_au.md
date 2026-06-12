---
title: "No repositories or adep manager after intalling automatix"
date: 2007-02-11
forum: Repositories &amp; Backports
---

### Post by tortugas09 on 2007-02-11
After several attempt to install automatix, I lost adept manager and the synaptic repositories When I try to use the adept manager; I get a message reading, "Failed to execute child process "kdesu" (No such file or directory).

When trying to open the synaptic package manager this message pops up, "E: Type 'gpg' is not known on line 38 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
.
When I go to the repository,I find it empty.

How do I reload the synaptic package manager and the adept manager without re-installing the operating system?
Any assistance would be of tremendous help.
Help?

---

### Post by meng on 2007-02-11
Are you sure it's empty? That doesn't sound right.

cat /etc/apt/sources.list

and post the result here.

---

