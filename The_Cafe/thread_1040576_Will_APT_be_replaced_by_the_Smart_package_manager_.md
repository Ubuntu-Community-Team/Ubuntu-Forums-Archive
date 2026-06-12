---
title: "Will APT be replaced by the Smart package manager backend?"
date: 2009-01-15
forum: The Cafe
---

### Post by Slug71 on 2009-01-15
Can't help but wonder if Smart package manager will become the default backend to Packagekit eventually and replace APT.

Canonical has been funding the project since 2005 and one of its lead devs has been contributing to the project along with input from devs from other Distros and projects.

Doesnt really make sense to fund something or help with a project if there is no intention to use it.

What do you guys think?

Link to Smarts Website for more info. Credits is right at the bottom of main page.
[http://labix.org/smart](http://labix.org/smart)


P.S. Does anyone know if Smart will be the default backend for F-11?

---

### Post by InfinityCircuit on 2009-01-15
Try using the "Search" feature. This came up a few weeks ago.

---

### Post by derekr44 on 2009-01-15
<silently chants "pacman... pacman... pacman">

---

### Post by InfinityCircuit on 2009-01-15
> **derekr44 said:**
> <silently chants "pacman... pacman... pacman">

You will get your wish...sort of.

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=511994](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=511994)

---

### Post by Polygon on 2009-01-15
unless debian switches, i am almost positive we will not switch. We do a complete sync with debian at the start of every development cycle. if we switch package managers with them, then complications are going to arise.

---

### Post by deepclutch on 2009-01-16
why dont APT developed more into the way you people want to ?

---

### Post by Namtabmai on 2009-01-16
Sorry but am I the only one confused by all these new "package managers". I've looked around a few, and where I can tried to check what benefits the author of the software feels it has over traditional package managers, but I just don't get it.

None of them seem to really do anything that would have real benefits, in fact several of them offer greater problems than the ones they are trying to solve.

---

### Post by Nepherte on 2009-01-16
What's wrong with apt? What's the advantage of smart?

---

### Post by bigbrovar on 2009-01-16
i think we should stick with apt .. we shouldn't always ditch something that  as been developed and proven to be stable and reliable for something which looks better from afar .. the grass is always greener on the other side .. i use pacman on arch and i think its an awesome package manager .. but after seeing what happened with pulse audio (which was suppose to improve things) i think Ubuntu should just stick with what works and improve on it. package management is a vital if not the backbone of a distro.. and switching to a completely diff Package manager would cause more problems then it would solve

---

### Post by bobbocanfly on 2009-01-16
If Debian were to switch (Exceptonally unlikely IMHO, I can't think of any reason they would want to switch to Pacman (and if they did want to switch, why they couldnt just update Debian packaging specs)) and then Ubuntu to switch with them, 95% of current distro packagers would be alienated and contribution to both projects would drop considerably until Pacman packagers appeared, or old dpkg packagers retrained.

IMHO a painfully bad move to make.

---

### Post by billgoldberg on 2009-01-16
> **bobbocanfly said:**
> If Debian were to switch (Exceptonally unlikely IMHO, I can't think of any reason they would want to switch to Pacman (and if they did want to switch, why they couldnt just update Debian packaging specs)) and then Ubuntu to switch with them, 95% of current distro packagers would be alienated and contribution to both projects would drop considerably until Pacman packagers appeared, or old dpkg packagers retrained.

IMHO a painfully bad move to make.

Indeed.

It could happen in the future, but not any time soon I guess.

---

### Post by derekr44 on 2009-01-16
I only picked Pacman because I'm biased to Arch :)

---

### Post by Slug71 on 2009-01-16
Heres a C/P of the Credits from Smarts website: As you can see people from Ubuntu, Debian, Mandriva, Fedora, Slackware and Synaptic and more have worked on this Project.

> Conectiva Inc. - Funded the creation of Smart, and its development up to August of 2005.
#

Canonical Ltd. - Is funding Smart development since September of 2005.
#

Wanderlei Cavassin - Conectiva's research & development coordinator, who belived the project was viable and encouraged the author to work on it.
#

Ednilson Miura & Herton Ronaldo Krzesinski - Conectiva employees, helped setting up many distributions for tests whenever necessary.
#

Andreas Hasenack - Conectiva employee, helped as being the first brave pre-alpha tester, and contributed with many ideas, discussions, etc.
#

Arnaldo Carvalho de Melo - Conectiva board member, helped with the "channel of mirrors" idea and by encouraging the author to build a generic channel.
#

Others @ Conectiva - Many other people in Conectiva helped with ideas and alpha-testing in general during the pre-release period of Smart development.
#

Guilerme Manika & Ruda Moura - Ancient Conectiva employees, now board members of the Haxent company, helped by testing Smart extensively in Fedora, reporting many bugs and suggesting changes. Also the original authors of the FAQ.
#

APT-RPM & Debian - Experience on packaging and ideas for a better framework were developed while the author of Smart worked as the APT-RPM maintainer.
#

Jeff Johnson - Contributed as being the RPM maintainer itself, and in many discussions regarding packaging theory in general.
#

Seth Vidal - YUM author, and member of the Duke University, contributed to Smart with the development of the XML MetaData repository format and discussions about it.
#

Michael Vogt - Currently the maintainer of the Synaptic, used to co-maintain it with the author of Smart. Many of his ideas ended up being adopted in Smart as a consequence.
#

Sebastian Heinlein - Author of the package icons for Synaptic, that were mercilessly stolen to be used in Smart's graphic interface.
#

TaQ/PiterPunk at #slackware-br - These guys helped Smart development by explaining details of Slackware practices regarding packaging.
#

Matt Zimmerman - Debian/Ubuntu developer and co-maintainer of the APT software, helped by shining some light regarding details of the DPKG pre-depends ordering expectations.
#

Mauricio Teixeira - FAQ maintenance, YaST2 channel maintainer, "tracker cleaner" ;), general suggestions and code contributions.
#

Jonathan Rocker - Documentation help. 

---

