---
title: "Get source code for all currently installed packags"
date: 2008-05-10
forum: The Cafe
---

### Post by maybeway36 on 2008-05-10
The GPL requires that if you distribute Ubuntu, you must either 1. provide a written offer to give the source code,
2. give them the source code, or
3. tell them where to get it - but ONLY if you are not selling anything.
If you wanted to sell someone computers with Ubuntu preinstalled, you would have to give them the source code. But how can you get the source code for every single package you have installed, after the updates are applied? That's where this script comes in.

The script options are:
iso - make a DVD ISO image to burn to a DVD (you must install genisoimage for this to work)
tar - make a tarball of the source code
plain - put the source code in a folder, so you can move it to /usr/local/src or somewhere else.

The script itself is licensed under the GPL, and is based on the live-helper project from Debian.

The script follows:
```
#!/bin/sh

# source-get - a source code downloader for Ubuntu
# Licensed under GPLv3

# based on live-helper's lh_source
## Copyright (C) 2006-2008 Daniel Baumann <daniel@debian.org>
##
## live-helper comes with ABSOLUTELY NO WARRANTY; for details see COPYING.
## This is free software, and you are welcome to redistribute it
## under certain conditions; see COPYING for details.

set -e

if [ -z $1 ];then
 echo "Usage:"
 echo "source-get [iso/tar/plain]"
 echo ""
 echo "iso   - makes a DVD source image"
 echo "tar   - makes a tar/gz archive"
 echo "plain - leaves the source directory alone"
 exit
fi

if [ ! -d source ] || [ -d source-working ];then

echo "Begin downloading sources..."

# Remove old sources
if [ -d source/ubuntu ]
then
	rm -rf source/ubuntu
fi
if [ -d source-working ]
then
	rm -rf source-working
fi

# Download sources
dpkg --get-selections | awk '{ print $1 }' > dpkg-selection.txt

mkdir source-working
cd source-working
xargs --arg-file=../dpkg-selection.txt apt-get --download-only source
cd ..
rm -f dpkg-selection.txt

# Sort sources
for DSC in source-working/*.dsc
do
	SOURCE="$(sed  -n 's|^Source: ||p' ${DSC})"

	case "${SOURCE}" in
		lib?*)
			LETTER="$(echo ${SOURCE} | sed 's|\(....\).*|\1|')"
			;;

		*)
			LETTER="$(echo ${SOURCE} | sed 's|\(.\).*|\1|')"
			;;
	esac

	# Install directory
	mkdir -p source/ubuntu/"${LETTER}"/"${SOURCE}"

	# Move files
	cp source-working/"${SOURCE}"_* source/ubuntu/"${LETTER}"/"${SOURCE}"
done

rm -r source-working

fi

if [ $1 = "tar" ];then
 echo "Begin building source tarball..."
 echo "This may take a while."
 # Remove old source
 if [ -f source.tar.gz ]
 then
  rm -f source.tar.gz
 fi
 # Create tarball
 tar cfz source.tar.gz source
 rm -r source
 fi

if [ $1 = "iso" ];then
 if [ -f /usr/bin/genisoimage ];then
  echo "Begin building source iso image..."
  # Remove old iso image
  if [ -f source.iso ]
  then
   rm -f source.iso
  fi
  genisoimage -o source.iso -r -J -l -cache-inodes source
  rm -r source
 else
  echo "Please install genisoimage."
 fi
fi

```

---

