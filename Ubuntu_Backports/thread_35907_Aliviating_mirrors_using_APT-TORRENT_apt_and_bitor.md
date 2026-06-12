---
title: "Aliviating mirrors using APT-TORRENT: apt and bitorrent"
date: 2005-05-20
forum: Ubuntu Backports
---

### Post by jobezone on 2005-05-20
To aliviate the backport mirrors, why not take look at apt-torrent. The project is still not 100% finished, it seems, but perhaps in the future it would be good to use? It can be used with any frontend wich uses apt:

" It can work with any program using apt as a backend like dselect/aptitude/synaptic/...etc."

Here is the documentation of it:
APT-TORRENT: "An apt proxy to bittorrent for Debian" - [http://sianka.free.fr/documentation.html](http://sianka.free.fr/documentation.html)

This are the most recent news of the developer:
"18/02/2005:
I'm currently looking for bandwidth to experiment deeply the project.
I'm considering setting up some mirrors with friends, anyway if you some ideas, do not hesitate share them with me.
I'll release a new version soon, so stay tunned."

Perhaps the backports main server could be the excellent testing ground that the developer is looking for?

---

### Post by jdong on 2005-05-20
Funny thing. Have you seen that I recently (within the past two days) put Apt-torrent into Hoary Extras Staging? ;)

I'll play with it a bit, and see if it's a practical solution

---

### Post by jobezone on 2005-05-20
Yes, actually I was looking at your site's statistics and saw in the changelog the inclusion of that package. I guess I forgot there would be a reason for you to be adding it to the backports :)
I also took the liberty to e-mail the developer of apt-torrent with this message:

"SUBJECT: Hello, I'm a user of Ubuntu, and would to point to you
a project called backports, which aims to maintain an
apt repository for recent packages for ubuntu.
The mirrors it uses are very much dried of all the
downloading they get, and apt-torrent would probably
be a good idea for them to try(in my view). And
perhaps you could make use of their bandwith for
testing of apt-proxy?

I'm not a developer of on backports, just wanted to
tell you about it. I've also added a thread talking
about apt-proxy in the backports forum:
[http://ubuntuforums.org/showthread.php?p=180663](http://ubuntuforums.org/showthread.php?p=180663) and if
you wish you could post in that forum, or contact the
backports developers directly:
[http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)

Thanks"
Hope you don't mind! What would make you refrain from using apt-torrent ? If the app is still under-developed? Because the idea and concept for me is excelent. People are already using bitorrent everywhere to distribute files and ISO's, like Canonical, for example, so why not use it for apt?

---

### Post by jdong on 2005-05-20
What's stopping me is two things:
[list=1]
[*]New technology. Nobody's used BT for apt-get before! I'm really curious how it works though. This isn't the major setback.   
[*]Ease/difficulty of setup. How difficult is it to teach new users how to add Apt-torrent and configure it. It's already enough of a pain explaining how to edit sources.list the way it is now. 
[/list] 

I think apt-torrent will be an EXCELLENT method of distributing backports, and I can't wait to get started testing it. I'm installing it as we speak.

---

### Post by jdong on 2005-05-20
I have contacted the author of apt-torrent, and I hope we can work together to make apt-torrent a distribution method for Backports.

---

### Post by jobezone on 2005-05-20
According to [http://sianka.free.fr/documentation.html](http://sianka.free.fr/documentation.html) the package will automatically add the necessary line in sources.list pointing to the local bitorrent proxy:

"# Local proxy
deb [http://127.0.0.1:6968/debian/](http://127.0.0.1:6968/debian/) unstable main"

The real repository is in /etc/apt/apt-torrent.conf so the package should be changed so it points to the backports HTTP server containing the .torrent files.

The .torrent files would then point to the backports apt-torrent-server which serves both as the tracker and a seeder.

Since this is automatically done by the package, the user wouldn't need to intervene in the process.

The questions which may be posed is concerning bitorrent itself and apt-proxy which is run as a deamon, both of wich I don't know much about.
I supose it will have the ability to serve files to other people using bitorrent as well, so it opens a port. What if users have that port closed in their routers? And is it(bitorrent) secure ? What about when a user is totally anaware of ports and just installed a raw Ubuntu?

And the most important question, is it spelled bitorrent or bittorrent??!

---

### Post by jobezone on 2005-05-20
Hmm, I found this discussion at the Debian-User mailing list [http://lists.debian.org/debian-devel/2004/10/msg01715.html](http://lists.debian.org/debian-devel/2004/10/msg01715.html):

> > Arnaud Kyheng wrote:
> | Hello,
> |
> | I love the Debian project, and I have worked on a new development
> | for it: Apt-Torrent :)
>
> Thank you for your contribution. However, I looked at doing
> something similar to this a little while ago and found that
> bittorrent is not very well suited for doing package downloads. Of
> the ~15k binary packages in Debian about 87% are under 1 meg in
> size and 98% are under 10 megs. The bit-torrent protocol works
> best on files significantly larger than this. Also, the protocol
> is not as efficient as it could be for the server hosting the
> .torrent file, which means it scales quite poorly when there are
> lots of requests for small files, as would be the case for Debian
> packages.

Someone else has also looked into adding a p2p protocal to apt file
fetching, haven't watched it closely, nor am I a developer for it.
[http://pdtp.org/static/](http://pdtp.org/static/)
At one point I thought they even had an apt-pdtp in the works, but i
can't find it now.
Not trying to say apt-torrent isn't a worthwhile project, but as Mike
noted, bittorrent really isn't a good protocal for the number of
small files Debian has. It does work well though for CD images.

Even it it wouldn't totally take away traffic from the server which seeds the packages, since most packages are indeed small, it would still be good for times when huge and popular packages get new versions, like Openoffice, or Firefox.

---

### Post by jobezone on 2005-05-20
More discussion of this between apt-torrent developer and debian people : [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=199316](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=199316)

---

### Post by vladanian on 2005-05-21
I don't see apt-torrent in hoary extras staging.

---

### Post by jdong on 2005-05-21
I've been looking into the source, and I've decided this is more trouble than it's worth.

We're getting two mirrors, which should give us plenty of bandwidth.


Meanwhile, I'll continue to distribute HUGE debs through decentralized Azureus.

---

