---
title: "How to search inside Binary Files and Devices"
date: 2012-06-28
forum: Tutorials
---

### Post by Sepero on 2012-06-28
Once in a while you might find the need to search inside of a binary file. For example, I once permanently deleted a text file on my system and needed to recover it. To do this I needed to search /dev/sda1 as root.

This can be done using the fast program- [SearchBin]("http://seperohacker.blogspot.com/2012/04/binary-grep-program-searchbin.html"). Download Link:
[http://seperohacker.blogspot.com/2012/04/binary-grep-program-searchbin.html](http://seperohacker.blogspot.com/2012/04/binary-grep-program-searchbin.html)

Using [SearchBin]("http://seperohacker.blogspot.com/2012/04/binary-grep-program-searchbin.html") you can search any binary data. You can search for a text string, hexidecimal bytes, or even another binary/text file.

To find my deleted file on the harddrive, I have to remember some of the text that was in the file, and search for that text.```
$ sudo ./searchbin.py -t "Hello there" /dev/sda1
Match at offset:           1881          759 in  /dev/sda1
Match at offset:           7284         1C74 in  /dev/sda1
Match at offset:           7420         1CFC in  /dev/sda1

```It will print out all the locations where "Hello there" is found. (Search is case sensitive) After you find the matching offset, you can open /dev/sda1 with a program like hexedit and copy out all the information you need. (Press Enter in hexedit to go directly to any offset)



This method can also be used for hacking game save files. If your character has 89 gold coins, then you will want to search for the hexidecimal of that number- 59 (be sure to make a backup of your game save) Hexedit the file to edit in whatever amount of gold/health/lives you want.
```
$ ./searchbin.py -p "59" gamesave.file
```



I once accidentally deleted an encrypted harddrive partition, and no rescue program can identify an encrypted partition. Luckily I had a copy of the first 512 bytes of the encrypted partition. Using [SearchBin]("http://seperohacker.blogspot.com/2012/04/binary-grep-program-searchbin.html"), I was able to find the location of my encrypted partition again and restore it fully!
```
$ sudo ./searchbin.py -f 512.head /dev/sda
```



For a skilled individual, there are a ton of potential uses with [SearchBin]("http://seperohacker.blogspot.com/2012/04/binary-grep-program-searchbin.html"). It's all up to your imagination.


Note:
Searching for raw files on your harddrive is not always fullproof, because files can become fragmented.

---

