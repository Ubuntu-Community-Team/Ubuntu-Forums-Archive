---
title: "DIY Ubuntu Repository on local server?"
date: 2012-02-18
forum: Server Platforms
---

### Post by pepsifx357 on 2012-02-18
Hey guys,

I've just set up a server using ClearOS(Based on Redhat/CentOS).  I use Ubuntu 10.04 for my workstations.  This is a nice server that I got for cheap on eBay.  It's got a 1.5 TB raid 5 Linux software array, 16GB of RAM and two quad core xeons.

I've already set it all up, except I've got to reinstall Ubuntu on a few machines that couldn't join the domain.

What I'm wanting to do is pretty obvious.  I play around with Ubuntu a LOT!  Adding removing splicing dicing.  I've been working on a Digital Audio Workstation build.  I need the Ubuntu repository to be on the local network using my new server.

I've read a few places on how to do this, but it's not what I want.  I might be thinking of Repository mirroring though...not sure.

What I want, is an Rsync script, or similar, that downloads, from an official repository, ALL packages available for Ubuntu 10.04.  These will reside on a file on the server.  My Ubuntu machines will be redirected via /etc/apt/sources.list to be pointed at my server.  Now it doesn't have to be strictly Rsync, however, I knew a Linux admin that helped me create one a couple of years ago.  It was a relatively simple Rsync line, that I in turn, changed into a script that was run once a day to update the servers files, on the internet, from an official repository.

I've since forgotten the lines of code for the command and I need some help replicating it, so that I can get this to work.

I really appreciate all the help!  All of the other solutions that I saw, were kinda mediocre in my opinion.

My normal repository that I use is located at [www.gtlib.gatech.edu](www.gtlib.gatech.edu)
  
Thanks!

EDIT
___________________________________________________________________________________________________________

I think I might have found something.

On the Mirror Scripts page on the Ubuntu wiki, I found this script.

```
#/bin/dash

fatal() {
  echo "$1"
  exit 1
}

warn() {
  echo "$1"
}

# Find a source mirror near you which supports rsync on
# https://launchpad.net/ubuntu/+archivemirrors
# rsync://<iso-country-code>.rsync.archive.ubuntu.com/ubuntu should always work
RSYNCSOURCE=rsync://archive.ubuntu.mirror.isp.com/ubuntu

# Define where you want the mirror-data to be on your mirror
BASEDIR=/var/www/ubuntuarchive/

if [ ! -d ${BASEDIR} ]; then
  warn "${BASEDIR} does not exist yet, trying to create it..."
  mkdir -p ${BASEDIR} || fatal "Creation of ${BASEDIR} failed."
fi

rsync --recursive --times --links --hard-links \
  --stats \
  --exclude "Packages*" --exclude "Sources*" \
  --exclude "Release*" \
  ${RSYNCSOURCE} ${BASEDIR} || fatal "First stage of sync failed."

rsync --recursive --times --links --hard-links \
  --stats --delete --delete-after \
  ${RSYNCSOURCE} ${BASEDIR} || fatal "Second stage of sync failed."

date -u > ${BASEDIR}/project/trace/$(hostname -f)
```

What I did was went to this page: [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors) and found the repository that I was using and verified that it was Rsync compatible.  Then, I changed the script to look like this.

```
#/bin/dash

fatal() {
  echo "$1"
  exit 1
}

warn() {
  echo "$1"
}

# Find a source mirror near you which supports rsync on
# https://launchpad.net/ubuntu/+archivemirrors
# rsync://<iso-country-code>.rsync.archive.ubuntu.com/ubuntu should always work
RSYNCSOURCE=rsync://rsync.gtlib.gatech.edu/ubuntu/

# Define where you want the mirror-data to be on your mirror
BASEDIR=/var/www/ubuntuarchive/

if [ ! -d ${BASEDIR} ]; then
  warn "${BASEDIR} does not exist yet, trying to create it..."
  mkdir -p ${BASEDIR} || fatal "Creation of ${BASEDIR} failed."
fi

rsync --recursive --times --links --hard-links \
  --stats \
  --exclude "Packages*" --exclude "Sources*" \
  --exclude "Release*" \
  ${RSYNCSOURCE} ${BASEDIR} || fatal "First stage of sync failed."

rsync --recursive --times --links --hard-links \
  --stats --delete --delete-after \
  ${RSYNCSOURCE} ${BASEDIR} || fatal "Second stage of sync failed."

date -u > ${BASEDIR}/project/trace/$(hostname -f)
```

I created the "ubuntu-archive" script in my /root directory, did a ```
sudo chmod +x ubuntu-archive
``` and ran the script, so we'll see what happens.

I looked at the /var/www/ folder and saw that it WAS, in fact, downloading the repository to the folder /var/www/ubuntu-archives/

I'm not sure exactly how my /etc/apt/sources.list should look after Its done downloading.  I'll fiddle with it when I get there.

EDIT-2
________________________________________________________________________________________

The only problem that I see, is that it is downloading hardy, maverick, natty, oneiric, and precise repositories as well.  I don't know how much space that takes up...lol

---

