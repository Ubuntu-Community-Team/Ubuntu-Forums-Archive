---
title: "Comments welcome: Nautilus ccrypt"
date: 2009-12-14
forum: Security
---

### Post by bryonak on 2009-12-14
I've been looking for a simple way suited for "non-techy" users to encrypt single files.
The default method in Ubuntu is to install seahorse-plugins, create a GPG key and use it after clicking on "Encrypt" in the context menu.
While you can go on and encrypt emails and such, I think it's a bit... "overkill" for someone who just wants to put a password on a file.
Mind you, my solution isn't any simpler... unless someone with enough experience cares to create a .deb package (with a ribbon) ;)

So I pulled inspiration from [here]("http://g-scripts.sourceforge.net/nautilus-scripts/File%20Processing/Misc/encryption") and from [here]("http://gnome-look.org/content/show.php/Encrypt%2BDecrypt?content=89310") and put together a small zenity+ccrypt+nautilus actions based encryption wrapper.

Here's the result: ccrypt-zenity
```

#!/bin/bash

######
# A zenity "front-end" for ccrypt
# For free use
# Move to /usr/bin and chmod 755
# Doesn't need any secure deletion tools like 'wipe' because it encrypts in-place
#
# Usage: ccrypt-zenity e filepath
#        ccrypt-zenity d filepath.cpt
#

mode=$1
file=$2
gui=`which zenity`
crypto=`which ccrypt`
ext="cpt"


# Check for existence of file and ask the user what to do
checkexist() {
	if [ -a "$checkfile" ]; then
		$gui  --title "Confirm File Replace!" --question --text="Target file already exists!  Delete the file $checkfile?"
		yesorno=$?
		if [ "$yesorno" == "1" ]; then
			exit 0
		else
			rm -f "$checkfile"
			if [ -a "$checkfile" ]; then
				$gui  --title "Operation Aborted!" --error --text="$checkfile could NOT be deleted!"
				exit 1
			fi
		fi
	fi
}

# Decrypt function
decrypt() {

	checkfile=${file%.$ext}
	checkexist

	p=`$gui --entry --hide-text --text='Enter password to decrypt' --title='Enter password'`

	$crypto -d -K $p "$file"

}

# Encrypt function
encrypt() {

	checkfile="$file.$ext"
	checkexist

	p=`$gui --entry --hide-text --text='Enter password to encrypt' --title='Enter password'`
	pr=`$gui --entry --hide-text --text='Repeat password' --title='Repeat password'`
	if [ $p != $pr ]; then
		$gui --info --title="Passwords don't match" --text="The entered passwords don't match"
		exit 0
	fi

	$crypto -e -K $p "$file"

}



if [[ -x "$gui" && -x "$crypto" && -e $file ]]; then
	if [[ $mode = 'e' ]]; then
		encrypt
	elif [[ $1 = 'd' ]]; then
		decrypt
	else
		$gui --title "Invalid Option!" --error --text="No valid option (e or d) specified!"
		exit 1
	fi
else
	if [[ -e $file ]];then
		result=""
	else
		result="File not found!; "
	fi
	if [ -x "$gui" ]; then
		result=`echo "$result"`
	else
		result="Zenity NOT found.  This utility is required!; "
	fi
	if [ -x "$" ]; then
		result=`echo "$result"`
	else
		result=`echo "$result ccrypt NOT found.  This utility is required! You can install it with your distribution's package manager (for example Synaptic).; "`
	fi
	echo $result
	$gui --title "Missing Required Tools!" --error --text="$result"
	exit 1
fi
exit 0

```

It has some checks but tries to be unobtrusive and simple.
ccrypt encrypts files "in place", which means it writes the encrypted blocks over the current file and there are no temporary files and other traces you have to delete with additional effort (i.e. using wipe). This also implies that you can only encrypt a single file at a time with the current code.
Multiple files and whole folders would have to get tar-ed and the intermediary archive cleanly deleted with wipe, but I'm keeping it simple for the first round.

This script is usable by any caller that can pass file paths as arguments, as for specific Nautilus integration I've attached two schemas you can import using Nautilus Actions.
They assume that you have copied ccrypt-zenity to /usr/bin. You will get a "Encrypt" option to the Nautilus context menu if you select a single file, plus a "Decrypt" option if you select a .cpt file.


About security: GPG creates 700+ bit keys by default, while ccrypt hashes the password to 256 bits. I hold the opinion that this is enough, yours may of course differ.
A short note on password vs key: if something is important enough to be encrypted, it's certainly important enough to be backed up. And encrypted data is useless without the key, which in turn means that the key is important enough to be backed up. And therefore secured with a password (we wouldn't let it lie around unencrypted, would we?).
So why not go with a password straight away?
Sure you could chose a "very safe" location for your key backup, but why not put the encrypted file there too then?
Now someone tell me if that just did make sense or if I'm missing something here :)

---

### Post by Sarmacid on 2009-12-14
Very nice, just want to comment on 2 things. You make a variable the path to zenity```
gui=`which zenity`
``` but you use just zenity on some lines, forgot to replace it?

I think when it doesn't find ccrypt it should output the command to get it```
sudo apt-get install ccrypt
```

---

### Post by bryonak on 2009-12-14
> **Sarmacid said:**
> Very nice, just want to comment on 2 things. You make a variable the path to zenity```
gui=`which zenity`
``` but you use just zenity on some lines, forgot to replace it?
Yes, thanks :)

> 
I think when it doesn't find ccrypt it should output the command to get it```
sudo apt-get install ccrypt
```
Good point, though I'd like to keep it a bit more general. Script updated.

---

### Post by jamily on 2010-02-18
One comment on the nautilus-action scripts for ccrypt: just like using ccrypt from the terminal, you should not include any spaces in your password (perhaps if you put your password in quotes?).  Otherwise the script (both encrypt and decrypt) will only parse the password until the first space.  For instance, you might think your password is

A friend in need is a pain indeed!

But your password really is

A

and "A" and "A friend in need is a pain indeed!" will both decrypt your file.

---

### Post by selinger on 2011-04-03
That's a common bash mistake. It should be "$p" in the script instead of $p, and similar for all the other variables (such as "$1", "$2", "$gui", "$crypto", even "${file%.$ext}" etc. All variables should be in double quotes unless you specifically want them to be broken into multiple words. 

Note that ccrypt has absolutely no problem handling passwords containing spaces; this is entirely a shell issue. Even passwords containing quotation marks are no problem. The following works without problems in bash:

p='This is a passphrase with    "strange" spaces and an odd number of " marks'
ccrypt -e -K "$p" "$file"
ccrypt -d -K "$p" "$file".cpt

-- Peter

---

