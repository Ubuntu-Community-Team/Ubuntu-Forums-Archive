---
title: "Using Script File to Download MP3 URLs"
date: 2012-12-21
forum: Server Platforms
---

### Post by Altin on 2012-12-21
I want to download podcast mp3s at night when my broadband connection is not otherwise being used. I wanted to save the links for the mp3s in a text file, one line for each link, on my Raspberry Pi home file server & use a script file to launch at a set time during the night, to begin downloading (wget) the mp3s on each line. 


With this method I would need the text file with my links, a script file & an 'at' command to launch the script file. Is this a good way to go about this? How would I write the script file commands too. Ive tried a few examples of script files through searches on the web but havent been able to get anything to run successfully.

Thanks

---

### Post by Habitual on 2012-12-21
I suggest cron.

Have a look at
[Download all mp3 on a webpage]("http://tech.karbassi.com/2009/09/29/download-all-mp3-on-a-webpage/")
[wget vs curl: How to Download Files Using wget and curl]("http://www.thegeekstuff.com/2012/07/wget-curl/")
[How can I use awk to extract URL's from a HTML file?]("http://unix.stackexchange.com/questions/56675/how-can-i-use-awk-to-extract-urls-from-a-html-file")

Various Linux Guides I have collected:
[http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html) 
[http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html) 
[http://tldp.org/HOWTO/Bash-Prompt-HOWTO/](http://tldp.org/HOWTO/Bash-Prompt-HOWTO/)
[http://www.gnu.org/software/bash/manual/html_node/index.html](http://www.gnu.org/software/bash/manual/html_node/index.html)
[http://www.grymoire.com/Unix/Sh.html](http://www.grymoire.com/Unix/Sh.html)
[http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html)
[http://tldp.org/LDP/abs/abs-guide.pdf](http://tldp.org/LDP/abs/abs-guide.pdf)
[http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/) 
[http://mywiki.wooledge.org/BashFAQ](http://mywiki.wooledge.org/BashFAQ)
[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)
[http://rute.2038bug.com/index.html.gz](http://rute.2038bug.com/index.html.gz)
[http://mylinuxbook.com/linux-shell-environment/](http://mylinuxbook.com/linux-shell-environment/)
[http://www.subsignal.org/doc/AliensBashTutorial.html#Table%20Of%20Contents](http://www.subsignal.org/doc/AliensBashTutorial.html#Table%20Of%20Contents)
[http://www.rigacci.org/docs/biblio/offline/TLCL-09.12.pdf](http://www.rigacci.org/docs/biblio/offline/TLCL-09.12.pdf)

---

### Post by spynappels on 2012-12-22
I suggest using a simple Bash script called from cron at whatever time you want, passing the full path to the URL list and the desired save location as arguments. The following might get you started:

```
#!/bin/bash

# Pass the path to the list of URLs as the first argument
# and the save location as the second argument

list=$1
loc=$2

cd $loc

for line in $(cat $list); do
    wget $line
done
exit
```

This can be improved on to check for arguments and if there is no second argument to use a default location etc.

This should give you a start anyway, if you need more help to expand this, just shout.

---

