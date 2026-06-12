---
title: "Worst command line mistakes?"
date: 2013-02-12
forum: The Cafe
---

### Post by basica on 2013-02-12
I'm sure this topic has been done to death, but I always find them interesting to read. Gives you a bit of a laugh and you can commiserate with others who too shared in your misery :)

I'll start off with a couple of stories:

1) The most recent one I made was deleting an entire folder by accident. I had a file called "test" and a folder called "Test". My alias is set up so that rm = rm -rf. I accidentally chose the wrong one and deleted a folder filled with scripts that I carelessly forgot to back up and had to rewrite from scratch. Since then I choose more colorful names than test/Test for my files and folders.

2) A few months ago I was editing some config file and before doing so I backed it up by renaming it and then creating a new one. After saving and testing the config file, I realised it wasn't going to work so I went to revert the changes. I hit the up keys and enter immediately without reading this: mv file.conf file.conf_backup. I overwrote my backup with the dodgy file. GRRR! :)

Anyways, would love to hear everyone elses! :)

---

### Post by unheeding on 2013-02-13
I meant to clear out all my settings from my home folder, and so I did a "rm -rf .*"


Or so I thought.  I actually forgot the period.  So it started deleting everything.  I lost everything in my Documents folder (no big deal, nothing important there).

---

### Post by lisati on 2013-02-13
I, too, have experienced the consequences of a misplaced rm command.....

---

### Post by fdrake on 2013-02-13
```
rm -R .*
```

---

### Post by mips on 2013-02-13
sudo dd if=/dev/sdc of=/dev/sde after a reboot and the devices were swapped around...

Should have confirmed the device identifiers after the reboot. Not really a cli mistake but still.

---

### Post by Elfy on 2013-02-13
Do you want to continue [Y/n]?Y

... I mean n

---

### Post by pqwoerituytrueiwoq on 2013-02-13
hitting enter after the 1st  slash  trying to type this [FONT=Courier New]sudo rm -rf /usr/local/share/my-script-files[/FONT]

---

### Post by rnerwein on 2013-02-13
> **basica said:**
> I'm sure this topic has been done to death, but I always find them interesting to read. Gives you a bit of a laugh and you can commiserate with others who too shared in your misery :)

I'll start off with a couple of stories:

1) The most recent one I made was deleting an entire folder by accident. I had a file called "test" and a folder called "Test". My alias is set up so that rm = rm -rf. I accidentally chose the wrong one and deleted a folder filled with scripts that I carelessly forgot to back up and had to rewrite from scratch. Since then I choose more colorful names than test/Test for my files and folders.

2) A few months ago I was editing some config file and before doing so I backed it up by renaming it and then creating a new one. After saving and testing the config file, I realised it wasn't going to work so I went to revert the changes. I hit the up keys and enter immediately without reading this: mv file.conf file.conf_backup. I overwrote my backup with the dodgy file. GRRR! :)

Anyways, would love to hear everyone elses! :)
hi
i think every one had problems with the rm on command line. my solution is expand your ~/.bashrc with

alias rm='rm_foo'

rm_foo()
{
echo -n "do really execute the rm ? (y/N) :"
read answer
# make N to the default
# here make your own script with the commands
case $answer in
    y) echo "ok now it is to late - i'll run $*";; # ......
    N) echo "oh - you used your brain - i don't run $*";;
    *) echo "the answer must be y or N"
esac
}
but remember this can give you problems with scripts !
cheers

---

