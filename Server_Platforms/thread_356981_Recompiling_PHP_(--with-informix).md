---
title: "Recompiling PHP (--with-informix)"
date: 2007-02-09
forum: Server Platforms
---

### Post by feenster on 2007-02-09
Hi all,
I'm working on a project that means I have to use an Informix database. I have tried to recompile PHP on our Ubuntu 6.06 LTS server using the "--with-informix=/opt/informix" command (and the Informix Client SDK *is* installed already).

However, i'm not getting anywhere as I cannot use the Informix functions, e.g. ifx_connect() without receiving an error.

My process was this:
1) Download and install the Informix SDK to /opt/informix
2) Use apt-get to download the PHP source to /usr/src/php5-5.1.2
3) Went into /usr/src/php5-5.1.2/debian and edited the file which lists the configuration options (can't remember it's name!). Added --with-informix=/opt/informix to this list
4) Ran ./configure
5) Ran ./make
6) Ran ./make install

But I still can't use the ifx() functions. Any ideas what I have done wrong?

Cheers,
   Matt

---

### Post by conjur3r on 2007-02-09
After reading your other thread about it working in CLI mode but not via apache ([http://www.ubuntuforums.org/showthread.php?t=357056)](http://www.ubuntuforums.org/showthread.php?t=357056)), create a php script in your htdocs directory and put <?php phpinfo(); ?>.  Navigate to it and see if it has included any of that informix stuff.  Also double check if the php.ini file is the correct one you're thinking of.

---

### Post by feenster on 2007-02-10
Hi,
Thanks for the reply. I have stuck a phpinfo() in htdocs, and whilst it mentions PDO_Informix, the Informix environment variables i added etc, it doesn't mention "--with-informix=/opt/informix" in the configure section. In fact, there isn't even a configure section! ;)

I have copied the cli php.ini file to the apache2 directory, so we are using exactly the same php.ini. Strange this. Kidders has give me some other things to try in the other thread, so i'll report back in both when i find something.

Cheers,
   Matt

---

### Post by solowookie on 2007-08-18
how did you get the client sdk installed?  I keep getting errors :confused:

---

### Post by feenster on 2007-08-19
Hi there,
Well, firstly i had to get the right CSDK. Not the RPM one, but the other type (sorry, can't remember the exact name!). Then i followed these instructions ([http://forums.gentoo.org/viewtopic.php?t=245249]("http://forums.gentoo.org/viewtopic.php?t=245249")) to use **cpio** to unpack stuff, then remove any references to the **c** parameter in the scripts. Once this was done, everything went in a treat!

Matt

---

### Post by solowookie on 2007-08-19
I was able to get it to install with no script modifications.  this is crude, but my basic install procedure.

sudo groupadd informix
sudo useradd -g informix -p xxxx -d /dev/null informix

export INFORMIXDIR=/opt/informix
export PATH=${INFORMIXDIR}/bin:${PATH}
export INFORMIXSERVER=m_srv
export INFORMIXSQLHOSTS=${INFORMIXDIR}/etc/sqlhosts
export LD_LIBRARY_PATH=${INFORMIXDIR}/lib:${INFORMIXDIR}/lib/cli:${INFORMIXDIR}/lib/esql:/compilers/SC3.0/lib:/usr/dt/lib

sudo mkdir /opt/informix
sudo chown -R informix.informix /opt/informix
copy sdk to /opt/informix
tar xvf *.tar
sudo ./install_rpm -acceptlicense=yes 
sudo ./installclientsdk


I have the procedures to complete integration of this with unixodbc if anybody wants them email me.

---

### Post by feenster on 2007-08-20
Nice one, simpler than my process. Hopefully, this thread will be of use for others in the future. Info was thin on the ground when i was doing it for the first time.

Matt

---

### Post by elmerjtuz on 2008-06-24
Hi 
I have installed the Informix SDK and I have all the environment variables set correctly. I have checked my connection to the informix server using dbaccess and the connection was successful, however when i Ran ./configure I got an warning saying :

Thank you for using PHP.

Notice: Following unknown configure options were used:

--with-informix=/opt/informix
 
 phpinfo() does not show any information about the --with-informix=/opt/informix. None of the informix functions are recognized by my installation.

Can anybody help me to solve this?

---

