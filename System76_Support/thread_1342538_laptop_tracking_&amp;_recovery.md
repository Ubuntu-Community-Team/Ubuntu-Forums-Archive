---
title: "laptop tracking &amp; recovery"
date: 2009-11-30
forum: System76 Support
---

### Post by dgermann on 2009-11-30
Hi--

Does System76 have or recommend software for tracking a laptop if it is lost or stolen?

I have gazv4 running 8.04.1.

Thanks!

---

### Post by Flying caveman on 2009-11-30
you could try this.  [http://www.linuxplanet.com/linuxplanet/tutorials/6744/1/](http://www.linuxplanet.com/linuxplanet/tutorials/6744/1/)

---

### Post by dgermann on 2009-11-30
Flying caveman--

Thanks!

Following your suggestion (the second page tells that the program there rarely works, can you believe it?!) I found this, which is a tape and string method of putting together one yourself: [http://www.helium.com/items/353689-how-to-set-up-a-lojack-for-your-linux-computer]("http://www.helium.com/items/353689-how-to-set-up-a-lojack-for-your-linux-computer")--it combines dynDNS and ddclient. Might be worth a trial if there is not something else out there that works well....

Thanks, Flying caveman!

---

### Post by jdb on 2009-11-30
> **dgermann said:**
> Flying caveman--

Thanks!

Following your suggestion (the second page tells that the program there rarely works, can you believe it?!) I found this, which is a tape and string method of putting together one yourself: [http://www.helium.com/items/353689-how-to-set-up-a-lojack-for-your-linux-computer]("http://www.helium.com/items/353689-how-to-set-up-a-lojack-for-your-linux-computer")--it combines dynDNS and ddclient. Might be worth a trial if there is not something else out there that works well....

Thanks, Flying caveman!

I could stand losing a computer, but I would hate to lose my data or
have my identity swiped.

I encrypt everything & keep encrypted copies in a lot of different places, other networked computers, removable devices, etc.
I've made scripts that do it for me.

jdb

---

### Post by dgermann on 2009-12-01
jdb--

Wonderful! Would you be willing to share your scripts?

Thanks, jdb!

---

### Post by samalex on 2009-12-01
I never thought of adding something like this to my system, so I'd be interested in doing something like this as well.  My only concern with taking the time to lojack my system is that if they don't have my password to login, they'd probably just throw in a Windows CD and reinstall the system overwriting my stuff anyway.  Some comfort is that the average thug probably has no knowledge of Linux or how to get my stuff off the system anyway, especially since Windows can't natively read the EXT3 or EXT4 file systems.  But I do need to research how to encrypt the critical data since my laptop is my primary system with EVERYTHING on it (taxes, banking, etc).

Take care --

Sam

---

### Post by jdb on 2009-12-01
> **dgermann said:**
> jdb--

Wonderful! Would you be willing to share your scripts?

Thanks, jdb!

I use crypsetup for encryption.
My main distro is ArchLinux, I encrypt root in that.
I don't encrypt Ubuntu root partitions, I use ext3 partitions & the
standard way of encrypting Ubuntu root requires an lvm partition.

Swap is randomly encrypted each boot.

crypttab
```
# <target name>	<source device>		<key file>	<options>
a7 /dev/sda7 /dog keyscript=/goat,cipher=aes-xts-plain,hash=whirlpool,size=512,swap

```

fstab
```
/dev/mapper/a7    none            swap    sw              0       0

```

I encrypt all other partitions except for /boot

Here is one of my backup scripts, it is very specialized for
my computers but it may give you some ideas.

dataBack
```
#dataBack               backs up data directory

if [ $# -ne 0 ]
	then
	echo "syntax: dataBack"
	exit 1
	fi

#date is YYYY_MM_DD
DATE=`date '+%Y_%m_%d'`

sudo -s dataBack1 $DATE


```

dataBack1
```
#dataBack1              called by dataBack

if [ `whoami` != root ] || [ $# -ne 1 ]
	then
	echo "syntax: dataBack1 YYYY_MM_DD"
	echo "must be root to run this, don't use sudo without -s"
	exit 1
	fi
	
IFS=$'\n'

function mnt
  {
  mount | grep -wq $1
  if [ $? -ne 0 ]
    then
    sudo mount /$1
    if [ $? -ne 0 ]
      then
      echo "can Not mount $1"
      exit 1
      fi
    fi
  }

mnt backup
mnt dogs
mnt boota
sudo rsync -ia --del /boota /backup

cd /

if [ `uname -n` == dads ]
  then
  mnt bootb
  mnt data
  mnt archives
  sudo rsync -ia --del /bootb /backup

  for x in `find data -maxdepth 1 -type d`
    do
    if [ "$x" != "data" ]\
					          && [ "${x#data/.}" == $x ]\
					          && [ "$x" != "data/lost+found" ]
	    then
	    if [ `find $x -type f \( -newer backup/dataBackSTAMP -o -cnewer backup/dataBackSTAMP \) | wc -l` -gt 0 ]
	      then
    	  cd data
        if [ "$x" == "data/sansaMusic" ] || [ "$x" == "data/music" ]\
                      || [ "$x" == "data/dp" ] || [ "$x" == "data/pictures" ]\
                      || [ "$x" == "data/multiMedia" ]  || [ "$x" == "data/applications" ]
          then
          s=""
          while [ -e "/backup/data/${x#data/}_$1$s.tg" ]
	          do
	          s="${s}_+"
	          done
          echo ${x#data/}_$1$s.tg
          tar cf "/backup/data/${x#data/}_$1$s.tg" "${x#data/}"
	        if [ $? -ne 0 ]
		        then
		        echo === ABORTED ABORTED ===
		        exit 1
		        fi
        else
          s=""
          while [ -e "/backup/data/${x#data/}_$1$s.tgz" ]
	          do
	          s="${s}_+"
	          done
          echo ${x#data/}_$1$s.tgz
          tar czf "/backup/data/${x#data/}_$1$s.tgz" "${x#data/}"
	        if [ $? -ne 0 ]
		        then
		        echo === ABORTED ABORTED ===
		        exit 1
		        fi
		      fi
        cd ..     
        fi
      fi
    done
  for x in `find archives -maxdepth 1 -type d`
    do
    if [ "$x" != "archives" ] && [ "$x" != "data/lost+found" ]
	    then
	    if [ `find $x -type f \( -newer backup/dataBackSTAMP -o -cnewer backup/dataBackSTAMP \) | wc -l` -gt 0 ]
	      then
    	  cd archives
        if [ "$x" == "archives/Willis" ] || [ "$x" == "archives/JPG" ]
          then
          s=""
          while [ -e "/backup/archives/${x#archives/}_$1$s.tg" ]
	          do
	          s="${s}_+"
	          done
          echo ${x#archives/}_$1$s.tg
          tar cf "/backup/archives/${x#archives/}_$1$s.tg" "${x#archives/}"
	        if [ $? -ne 0 ]
		        then
		        echo === ABORTED ABORTED ===
		        exit 1
		        fi
        else
          s=""
          while [ -e "/backup/archives/${x#archives/}_$1$s.tgz" ]
	          do
	          s="${s}_+"
	          done
          echo ${x#archives/}_$1$s.tgz
          tar czf "/backup/archives/${x#archives/}_$1$s.tgz" "${x#archives/}"
	        if [ $? -ne 0 ]
		        then
		        echo === ABORTED ABORTED ===
		        exit 1
		        fi
		      fi
        cd ..     
        fi
      fi
    done
  fi

for x in `find dogs -maxdepth 1 -type d`
  do
  if [ "$x" != "dogs" ]
	  then
	  if [ `find $x -type f \( -newer backup/dataBackSTAMP -o -cnewer backup/dataBackSTAMP \) | wc -l` -gt 0 ]
	    then
  	  cd dogs
      if [ "$x" == "dogs/pkg" ]
        then
        s=""
        while [ -e "/backup/dogs/${x#dogs/}_$1$s.tg" ]
	        do
	        s="${s}_+"
	        done
        echo ${x#dogs/}_$1$s.tg
        tar cf "/backup/dogs/${x#dogs/}_$1$s.tg" "${x#dogs/}"
	      if [ $? -ne 0 ]
		      then
		      echo === ABORTED ABORTED ===
		      exit 1
		      fi
      elif [ "$x" == "dogs/VirtualBox" ] ||  [ "$x" == "dogs/gits" ]
        then
        s=""
        while [ -e "/backup/dogs/${x#dogs/}_$1$s.tgz" ]
	        do
	        s="${s}_+"
	        done
        echo ${x#dogs/}_$1$s.tgz
        tar czf "/backup/dogs/${x#dogs/}_$1$s.tgz" "${x#dogs/}"
	      if [ $? -ne 0 ]
		      then
		      echo === ABORTED ABORTED ===
		      exit 1
		      fi
		    fi
      cd ..     
      fi
    fi
  done

touch backup/dataBackSTAMP

```

jdb

---

### Post by dgermann on 2009-12-01
samalex--

Yes, you are probably right.

I am looking into truecrypt which a lot of people here talk about.

Thanks, Alex!

jdb--

Wow! It'll take me some time to work my way through those scripts. Thanks much!

---

