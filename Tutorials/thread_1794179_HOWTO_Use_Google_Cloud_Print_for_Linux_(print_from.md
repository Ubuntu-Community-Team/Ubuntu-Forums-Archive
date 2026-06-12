---
title: "HOWTO: Use Google Cloud Print for Linux (print from Andriod device)"
date: 2011-06-30
forum: Tutorials
---

### Post by bferd on 2011-06-30
[SIZE=4]**See znote's post below to get this to work with the latest version of python. I'll update the how to to reflect the changes later. Right now I just don't have time.**[/SIZE]

[SIZE=4]**T**[/SIZE][SIZE=2]his[/SIZE] tutorial will allow you to print from anywhere to your home printer using your android device via Google Cloud Print for Linux.


***Notes***

It is best to set this up on a home server or another computer that runs all the time, as the printer will only be "online" when your computer is running.
You can use either a wired or wireless printer, or a network printer.

I did not make this script, I just tested it out using instructions found from various other pages (see references below,) and this is how I did it.

Credit goes to [wasserkapf]("http://forum.xda-developers.com/member.php?u=2927720") at the xdadevelopers forum for most of the instruction.


[COLOR=Red]***Important***[/COLOR]

Before beginning ensure that the printer that you want to share is set up in Ubuntu and that you can actually print from it. If this is not the case this tutorial won't work.


***Set up your Ubuntu box to use Google Cloud Print***

Use GIT to download the source. To use GIT, you first need it installed. You also need python and python-cups installed

```

sudo apt-get install git-core python python-cups

```Now use git to download the source code to your home folder

```

git clone git://github.com/armooo/cloudprint.git

```change permissions of the downloaded folder

```

chmod -R 777 ~/cloudprint

```Now change directory to the cloudprint folder

```

cd ~/cloudprint

```run the setup.py script

```

python setup.py build

```Now install Google Cloud Print for Linux

```

sudo python setup.py install

```This installed the script in this folder

/usr/local/lib/python2.6/dist-packages/cloudprint/cloudprint.py

Run it and it will ask for your Gmail address and password

```

python /usr/local/lib/python2.6/dist-packages/cloudprint/cloudprint.py

```It will also add your default printer. 

You can manage your printers at the following address.

[http://www.google.com/cloudprint/manage.html](http://www.google.com/cloudprint/manage.html)



***Set Up your Android Device***

There are two programs that you can use to do this. I prefer "PrinterShare", but you can also use "Cloud Print". PrinterShare (free version) does not allow you to print directly to your networked printer without going through Google Cloud Print. I find the delay minimal and out-weigh the advertisements in the Cloud Print program.

go to your market app and search for either "PrinterShare" or "Cloud Print" and install. Or you can use the links below.

[https://market.android.com/details?id=com.dynamixsoftware.printershare&feature=search_result](https://market.android.com/details?id=com.dynamixsoftware.printershare&feature=search_result)

[https://market.android.com/search?q=cloud+print&so=1&c=apps](https://market.android.com/search?q=cloud+print&so=1&c=apps)

Both programs are easy to set up.

To print use your "Share" button on your Android device and select "PrinterShare" or "Cloud Print"



***References***

[http://forum.xda-developers.com/showthread.php?t=950312&highlight=cloudprint](http://forum.xda-developers.com/showthread.php?t=950312&highlight=cloudprint)
[http://blog.nguyenvq.com/2011/05/12/google-cloudprint-on-linux/](http://blog.nguyenvq.com/2011/05/12/google-cloudprint-on-linux/)
[http://www.linuxquestions.org/linux/answers/applications_gui_multimedia/howto_use_google_cloud_print_linux](http://www.linuxquestions.org/linux/answers/applications_gui_multimedia/howto_use_google_cloud_print_linux)
[https://github.com/armooo/cloudprint](https://github.com/armooo/cloudprint)
[http://forum.xda-developers.com/showthread.php?t=991772](http://forum.xda-developers.com/showthread.php?t=991772)

---

### Post by geazzy on 2011-07-02
great job bro :guitar:

---

### Post by MrEgg on 2011-07-02
Works great! Thanks!!

---

### Post by Minime1 on 2011-07-10
Very nice indeed. Have been looking for a way to do this and even google's pages don't mention anything about Linux, only Windoze and Mac. Good Job :cool:

---

### Post by znote on 2011-12-21
hi great script.
I had to change this in ez_setup.py to get it workin
---
import sys
DEFAULT_VERSION = "0.6c11"
DEFAULT_URL     = "http://pypi.python.org/packages/2.7/s/setuptools/setuptools-0.6c11-py2.7.egg"

md5_data = {
    'setuptools-0.6c11-py2.7.egg': 
'fe1f997bc722265116870bc7919059ea'
}

---

and i had to change this line from the guide

python /usr/local/lib/python2.6/dist-packages/cloudprint/cloudprint.py

to 

python /usr/local/lib/python2.7/dist-packages/cloudprint/cloudprint.py

---

### Post by bferd on 2011-12-21
At a boy. It actually broke a while ago and I've been so busy I haven&#8217;t had time to even think about looking into it.

---

### Post by ttguy on 2012-01-09
This worked for me too - following the Znotes updates. For some reason though I had to manually download the [setuptools-0.6c11-py2.7.egg]("http://pypi.python.org/packages/2.7/s/setuptools/setuptools-0.6c11-py2.7.egg")   from [http://pypi.python.org/packages/2.7/s/setuptools/](http://pypi.python.org/packages/2.7/s/setuptools/)

So am I correct in assuming that I need to keep the cloudprint.py terminal window open to have this running?  

Any hints on how to make this start up every time I boot up my Ubuntu box ?

---

### Post by TotalN0ob on 2012-01-12
getting this error: > Package git-core is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'git-core' has no installation candidate

getting it on the first input in terminal.

---

### Post by Paul Mitchell on 2012-03-28
> **ttguy said:**
> This worked for me too - following the Znotes updates. For some reason though I had to manually download the [setuptools-0.6c11-py2.7.egg]("http://pypi.python.org/packages/2.7/s/setuptools/setuptools-0.6c11-py2.7.egg")   from [http://pypi.python.org/packages/2.7/s/setuptools/](http://pypi.python.org/packages/2.7/s/setuptools/)

So am I correct in assuming that I need to keep the cloudprint.py terminal window open to have this running?  

Any hints on how to make this start up every time I boot up my Ubuntu box ?

I just added the following line to /etc/rc.local

```
/usr/bin/python /usr/local/lib/python2.6/dist-packages/cloudprint/cloudprint.py >> /var/log/cloudprint.log 2>&1 &
```

---

### Post by grrrb on 2012-04-06
Thanks, it works great! Using the commandline as root without the  redirect to log shows info about printer and prints, but using it with  >> logfile 2>&1 & doesn't log anymore. No big deal.

---

### Post by bferd on 2012-11-30
This still works with the latest version of Ubuntu. I'll update the "how to" once i get enough posts to allow editing again.:-P

---

### Post by jboehm on 2013-06-02
See
[http://blog.rebeiro.net/2012/12/google-cloud-print-daemon-for-ubuntu.html](http://blog.rebeiro.net/2012/12/google-cloud-print-daemon-for-ubuntu.html)

---

### Post by metalgoldphish on 2014-03-20
hey there, trying to follow this tutorial, 

i get this error

Installed /usr/local/lib/python2.7/dist-packages/cloudprint-0.11-py2.7.egg
Processing dependencies for cloudprint==0.11
Finished processing dependencies for cloudprint==0.11
root@house-01:~/cloudprint# python /usr/local/lib/python2.7/dist-packages/cloudprint/cloudprint.py
python: can't open file '/usr/local/lib/python2.7/dist-packages/cloudprint/cloudprint.py': [Errno 2] No such file or directory
root@house-01:~/cloudprint# 


the reason i am currently in root is i thought it may be the problem, i tried the same earlier without being logged in as  root and got the same results.. 
any ideas? 

also navigated to the folder, ther is no cloudprint.py file available, it seems to still be in a zip (.egg) folder that it wont let me extract to the folder

help please.
thank you

---

### Post by tim84 on 2015-01-09
This looks like a very helpful script!  However, I'm in the same boat as metalgoldphish.  I'm guessing that just a line or two of code are off.  I'm currently running Natty 11.04.  Has anyone resolved this?  Thanks in advance!

---

### Post by emreceb on 2015-09-01
+1 No such file or directory

---

