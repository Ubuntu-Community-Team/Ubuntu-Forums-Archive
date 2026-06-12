---
title: "A simple /etc/hosts updater script"
date: 2010-12-29
forum: Security
---

### Post by ljhffmn on 2010-12-29
This is my first posting so forgive me if I've put it in the wrong place or some such thing. Here's a simple script I put together to update a hosts file to contain a whole lot of 0.0.0.0 redirects of known hostile addresses.
```

#!/bin/bash								

#~#~#~#~#~#~#~#~#~#~#~#~#~#~#~#~#~#~#~#~#~#~#~#~#~#~#~#~#~#~#~#~#~#~#~#~#
# update-hosts.sh							#
# Written by Lawrence Hoffman 						#
# Mon Dec 27 12:07 AKST 2010						#
# This is a very rudimentary bash script for updating a linux hosts	#
# file. For questions or comments contact the author at 		#
# lawrence@lawrencehoffman.net						#
#~#~#~#~#~#~#~#~#~#~#~#~#~#~#~#~#~#~#~#~#~#~#~#~#~#~#~#~#~#~#~#~#~#~#~#~#

echo # Drop down a line before we start for readability
echo "update-hosts.sh By Lawrence Hoffman (lawrence@lawrencehoffman.net)"
echo "ENJOY!"; echo;

# Check that we're in a BASH shell
if test -z "$BASH" ; then
  echo "update-hosts.sh must be run in the BASH shell... Aborting."; echo;
  exit 192
fi

# Check for root user
if [ $(whoami) != "root" ]; then
  echo "update-hosts.sh must be run as root... Aborting."; echo;
  exit 192
fi

# Sanity checks:
echo "Checking that all required software is installed."; echo;
type -P wget &>/dev/null || { echo "Error: update-hosts.sh requires the program wget... Aborting."; echo; exit 192; }
type -P sed &>/dev/null  || { echo "Error: update-hosts.sh requires the program sed... Aborting."; echo;exit 192; }
type -P date &>/dev/null || { echo "Error: update-hosts.sh requires the program date... Aborting."; echo; exit 192; }

# Back up host file:
echo "Creating a backup of /etc/hosts in the file /etc/ORIGHOSTS"; echo;
cat /etc/hosts > /etc/ORIGHOSTS

# Download updated hosts file
echo "Downloding file at http://www.mvps.org/winhelp2002/hosts.txt";
wget --quiet http://www.mvps.org/winhelp2002/hosts.txt --directory-prefix=/etc/; echo;

# Format new hosts file
echo "Formatting... "; echo;
sed -i -n -e 's/127.0.0.1/0.0.0.0/p' /etc/hosts.txt 
sed -i -e '/localhost/d' /etc/hosts.txt

# Delete old Addblock
echo "Updating... "; echo;
sed -i -e '/update-hosts.sh/d' /etc/hosts
sed -i -e '/0.0.0.0/d' /etc/hosts

# Install new Addblock
UPDATESTR="# update-hosts.sh last update $(date) #"
echo $UPDATESTR >> /etc/hosts
cat /etc/hosts.txt >> /etc/hosts

# Clean up
echo "Cleaning up..."; echo;
rm /etc/hosts.txt

# Exit clean
echo "update-hosts.sh update complete."; echo;
exit 0

```
This script creates a back up of your last hosts file in /etc/ORIGHOSTS. I hope someone finds this usefull.

---

### Post by robert_pectol on 2010-12-29
Nice script!  You could also change the 0.0.0.0 to the IP of a local pixel server.  That way you won't get missing graphics, 404s, and empty frames.  The local pixel server simply delivers a 1x1 pixel transparent gif for any http request, be it a document, graphic, etc.  Combined with your script, this makes a very effective ad blocking solution.  I have this set up on my router and it really works.  It also speeds up browsing and saves bandwidth because you aren't downloading and displaying all the ad material that gets thrown at you!  The pixel server is a simple Perl script found here:
[http://proxytunnel.sourceforge.net/files/pixelserv.pl.txt](http://proxytunnel.sourceforge.net/files/pixelserv.pl.txt)
There's also an inetd version of it if you prefer. Anyway, thanks for sharing.

---

### Post by ljhffmn on 2010-12-29
Robert,
Thank you for the advice on the pixel server. That's an idea I'm going to have to try out. I'm glad I made this post.

---

### Post by crosenblum on 2012-04-27
I really like your script. 

Just out of curiousity, is there a way to make it compress the hosts file lines?

I remember this application in window's, that would take 4 host file lines and make them 1 line, so the hosts file would take less space, and less file space.

But i am not sure of the validity of that format working in linux. If it does, is that a valid way to reduce file space usage by huge hosts file?

Since hosts file are a neat and cheap way to block stuff on the internet.

btw, thanks again for the nice script.

---

### Post by CharlesA on 2012-04-27
You would have to do it manually because it grabs a hosts file from an external source and just imports them.

---

