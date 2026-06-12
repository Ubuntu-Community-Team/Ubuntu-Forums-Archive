---
title: "software app no apps and picasa and skype missing from repos."
date: 2016-07-05
forum: Ubuntu Studio
---

### Post by Mickeyj4j on 2016-07-05
Hi I have recently installed Ubuntu Studio 16.04. the first thing i looked for was synaptic which was not installed. so i used software app. but that has nothing in it.  i installed synaptic via command line. so i can install apps. 

compared to ubuntu and linux mint previous linux os i have tried. there are some things missing picasa and skype. 

i went to the skype website and got the skype app but when trying to install that. it opened the install app but just sat there for 30 mins not doing anything. 

so i ran 
sudo  dpkg -i /path/to/skype.deb/file (installed with errors)
then i ran 
sudo apt-get install -f (this fixed and i got skype) 

I tryed the same with picasa i got the picasa.deb file from the ubuntu website. but the latest package was for Petra adn did not work. 

any ideas how to get this installed.

---

### Post by ajgreeny on 2016-07-05
Are you using Mint; you talk of Petra, which is a Mint version?

Picasa is no longer developed, and been replaced as far as I'm aware by google-photos, though you may be able to still download the 3.9 version for Windows XP & 7 from [https://picasa.google.co.uk/](https://picasa.google.co.uk/) but you will have to run it with wine.

Skype is available with the package manager if you enable the canonical-partner repos in your software-sources, but I have no idea how you find them in Mint; presumably just the same as Ubuntu.

---

