---
title: "Create an encrypted backup"
date: 2008-10-18
forum: Security
---

### Post by u-slayer on 2008-10-18
_Read below for "Completed" script_
[post 5]("http://ubuntuforums.org/showthread.php?p=5992159#post5992159")

---

### Post by u-slayer on 2008-10-18
NVM I figured it out.

I wrote a quick batch script. I'll figure out how to decrypt later.

```
#Defaults
encryption="AES256"

#Get Options
while getopts 'e:v' OPTION
do
  case $OPTION in
  e)	encryption=$OPTARG;;
  v)	verbose=1;;
  ?)	print_usage; exit 2;;
  esac
done
shift $(($OPTIND - 1))

output=`echo $* | sed 's/^.* //'`
input=`echo $* | sed 's/ .*//'`

#pass=`randomkey`
pass=`dd if=/dev/random bs=4 count=8 2>/dev/null | xxd -p -c 256 | head -c 64`

tar -cjvf - $input --to-stdout | gpg --symmetric --cipher-algo $encryption --passphrase $pass - > $output

echo $pass 1>&2

#Cleanup
pass=0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
```

---

### Post by kevdog on 2008-10-18
Are you sure that passphrase will be valid later -- meaning you will remember it??

I wrote a similar script -- perhaps yours is better.  Perhaps you could improve mine.  Here is my thread where I gave my ideas however I was looking for a way to protect the password from being in memory:

[http://ubuntuforums.org/showthread.php?t=939545](http://ubuntuforums.org/showthread.php?t=939545)

---

### Post by u-slayer on 2008-10-19
> **kevdog said:**
> I was looking for a way to protect the password from being in memory:

I don't believe it is possible to keep the password out of system memory, the decryption code has to have the key at some point. All we can do is overwrite the password in memory when the script has finished.

> Are you sure that passphrase will be valid later -- meaning you will remember it??

I never intended to memorize it. I always have a truecrypt volume mounted for secret keys and such. Here is how I use my script..

```
./ce pathname [ pathname ... ] outputFile > /mnt/key.txt
```

The password generated is 64 Hex chars long. 64*(4 bits)=256 bits - An extremely Strong password.

---

### Post by u-slayer on 2008-10-19
Okay I added decrypt ability to my script.

To Compress and Encrypt a directory into a file...

```
./ce pathname [ pathname ... ] outputFile 
```

The key is written to stdout. You can redirect it into a file if you wish.

To Decrypt and Decompress a file into the current directory...
```
./ce inputFile
```

```
#Default Options
encryption="AES256"
#pass=`randomkey`
pass=`dd if=/dev/random bs=4 count=8 2>&1 | sha256sum | head -c 64`
compression="bzip2"
v="v"	#verbosity

#Get Options
while getopts 'e:p:c:qv' OPTION
do
  case $OPTION in
  e)	encryption=$OPTARG;;
  c)	compression=$OPTARG;;
  p)	pass=$OPTARG;;
  q)	v="";;
  v)	v="vv";;
  ?)	print_usage; exit 2;;
  esac
done
shift $(($OPTIND - 1))

input=`echo $* | sed 's/ .*//'`
output=`echo $* | sed 's/^.* //'`

if [ `echo $input | wc -w` == "1" -a -f "$input" ]; then
	mode=d
else
	mode=e
fi

if [ $mode == "e" ]; then		#Encrypt Mode
	tar --to-stdout --$compression -c"$v"f - $input |\
		gpg --symmetric --cipher-algo $encryption --passphrase $pass - > $output
	
	echo $pass

else					#Decrypt Mode
	gpg -d $input | tar --$compression -x"$v"f -
fi



#Cleanup
pass=0000000000000000000000000000000000000000000000000000000000000000
```

---

### Post by hyper_ch on 2008-10-19
I'd either use this:

[http://www.howtoforge.com/ftp-backups-with-duplicity-ftplicity-debian-etch](http://www.howtoforge.com/ftp-backups-with-duplicity-ftplicity-debian-etch)

or (as I do now): I just backup onto a fully encrypted system.

---

### Post by chmac on 2008-12-15
I agree, I think duplicity is a better option for most people. The script in this thread is a useful example to show what's possible, but for the average user, duplicity is an `apt-get install duplicity` away and easier to work with.

---

### Post by jcsteele on 2008-12-15
Anyone utilize GnuPG for something similar yet?

---

### Post by Chayak on 2008-12-15
> **jcsteele said:**
> Anyone utilize GnuPG for something similar yet?

Duplicity does have GPG encryption as an option.  It works better than the script because it will encrypt to a public key so you don't have to type anything in or leave the key in a script to get it to work.

---

### Post by chmac on 2008-12-16
> **Chayak said:**
> Duplicity does have GPG encryption as an option.  It works better than the script because it will encrypt to a public key so you don't have to type anything in or leave the key in a script to get it to work.

It's true that duplicity can encrypt with a public key. However, I believe it needs the password for the private key. My (limited) understanding from using it some time ago is that it creates a series of specially formatted tar files which it encrypts and then uploads. In order to make differential backups, it downloads some data from the server, decrypts it, and then uses that data to create a new, encrypted, differential backup.

I don't think it's possible to run duplicity without providing a password, although the password can be provided through an environment variable for unattended operation.

---

### Post by hyper_ch on 2008-12-16
as far as I understand it, duplicity will keep list of what has been backed up on the local computer. So it will not download stuff from the server and decrypt it.

---

### Post by chmac on 2008-12-16
> **hyper_ch said:**
> as far as I understand it, duplicity will keep list of what has been backed up on the local computer. So it will not download stuff from the server and decrypt it.

You're absolutely right. I've just done a local test and confirmed that by using the --archive-dir and --encrypt-key options, duplicity can create encrypted backups remotely without the need for a passphrase. Fantastic!

```
duplicity --archive-dir /path/to/local/duplicity/archive/ --encrypt-key XXXXXXXX /home/me/tmp/test/ file:///home/me/tmp/backup/
```

---

