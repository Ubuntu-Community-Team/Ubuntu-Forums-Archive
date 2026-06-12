---
title: "Script to add multiple lines of text to a text file"
date: 2010-12-03
forum: The Cafe
---

### Post by Kangarooo on 2010-12-03
**Can we do some day collaborative editing making screencast for setting up collaborative workspace and actual collaboration? See [https://docs.google.com/document/d/1SmZo8QqyFNcge2vUsmwoBrj3CZ71y4ur-HwRW7lWH68/edit?hl=en&authkey=COSfvIcJ](https://docs.google.com/document/d/1SmZo8QqyFNcge2vUsmwoBrj3CZ71y4ur-HwRW7lWH68/edit?hl=en&authkey=COSfvIcJ)**


[http://ubuntuforums.org/showthread.php?t=536920](http://ubuntuforums.org/showthread.php?t=536920)
if echo "blabla" | tee -a file.txt
and echo "first line\nsecond line" (as mentioned there actually doesn work)
but works echo $'first line\nsecond line'
then why isnt 

```
echo "alias upup='sudo aptitude update && sudo aptitude dist-upgrade'\nalias inin='sudo aptitude -y install'\nalias search='apt-cache search'\nalias pupu='sudo aptitude purge'" | tee -a .bashrc
```
```
echo $"alias upup='sudo aptitude update && sudo aptitude dist-upgrade'\nalias inin='sudo aptitude -y install'\nalias search='apt-cache search'\nalias pupu='sudo aptitude purge'"
```
```
echo $'alias upup='sudo aptitude update && sudo aptitude dist-upgrade'\nalias inin='sudo aptitude -y install'\nalias search='apt-cache search'\nalias pupu='sudo aptitude purge''
```



actually i would like to make a script so that
user can choose what alias he wants and what names
lets try collaborate in [https://docs.google.com/document/d/1SmZo8QqyFNcge2vUsmwoBrj3CZ71y4ur-HwRW7lWH68/edit?hl=en&authkey=COSfvIcJ](https://docs.google.com/document/d/1SmZo8QqyFNcge2vUsmwoBrj3CZ71y4ur-HwRW7lWH68/edit?hl=en&authkey=COSfvIcJ)
like
executing alias.sh all
would ask does he wants 1 apt-get or 2 aptitude:
if aptitude then if programm uninstalled then line witch will be added to alias would be with checking if aptitude is there for only purge command if its also checked to be added to alias bashrc
so next questions are witch commands u want to add 1 update && dist-upgrade 2 install 3 purge 4 remove 5 search add seperated with commans or all:all
then do you want to change some names of commands 1 no 2 yes:
then witch ones (reading from variables) 1 update && dist-upgrade 2 install 3 purge 4 remove 5 search or all: 1,3
so then enter name for alias for x1:
x2:
is this ok 1 yes 2 change alias (goes to previous) 3 add allias 4 remove alias:
then if 1 the executed echo $"alias $x1='blabla'\nalias #x2='blabla install'"

executing alias.sh new
would ask what alias u want and for what command.


commands needed for alias.sh all
$1c=sudo $ap update && sudo $ap dist-upgrade
$2c=sudo $ap install
$3c=sudo $ap purge
$4c=sudo $ap remove
$5c=apt-cache search

$1n=update
$2n=install
$3n=purge
$4n=remove
$5n=search

$ap=aptitude or if not installed then no option if installed then echo checking aptitude installation
apt-get
aptitude

---

