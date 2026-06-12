---
title: "File transfer to server"
date: 2012-02-16
forum: Server Platforms
---

### Post by paulwilson5x on 2012-02-16
Im running ubuntu server 11.10, im creating a website and dont know how to put pictures into the website. Please help

---

### Post by paulwilson5x on 2012-02-16
Im running ubuntu server 11.10, making a website, how do i get images (.jpeg .gif etc) onto the server? please help

---

### Post by cariboo on 2012-02-16
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by haqking on 2012-02-16
broad non specific question.

From where ?

using what ? (USB, NFS, Internet like wget ?

etc etc

---

### Post by winh8r on 2012-02-16
Lots of good info and how-to guides can be found here:

[http://www.thefreecountry.com/]("http://www.thefreecountry.com/")


Or if you can be a bit more specific about the issue you are having maybe someone here can offer some advice.

Hope this is of some help to you.

---

### Post by paulwilson5x on 2012-02-17
I would like to get pictures from a file I have on my ubuntu desktop. I also have the pictures on a usb so either would be fine

---

### Post by haqking on 2012-02-17
> **paulwilson5x said:**
> I would like to get pictures from a file I have on my ubuntu desktop. I also have the pictures on a usb so either would be fine

you mean pictures from a folder or a file ?

and we still need more information.

if the files are on your USB then stick the USB in the server and copy the files over.

so you have 2 physical machines ?

be more specific

---

### Post by winh8r on 2012-02-17
To upload images to your website from your local desktop you could use something like 


filezilla


you can install filezilla using the terminal

```
sudo apt-get install filezilla
```


A how to can be found at the site I referred you to yesterday:


[http://www.thesitewizard.com/gettingstarted/howtoupload.shtml]("http://www.thesitewizard.com/gettingstarted/howtoupload.shtml")




Hope this helps you

---

### Post by paulwilson5x on 2012-02-17
ok sorry, Im using virtual box on a windows machine. In virtual box I have the ubuntu desktop and server. The images on the ubuntu desktop are in /home/images.

---

### Post by haqking on 2012-02-17
> **paulwilson5x said:**
> ok sorry, Im using virtual box on a windows machine. In virtual box I have the ubuntu desktop and server. The images on the ubuntu desktop are in /home/images.

use shared folders to share between the virtual machines then. [http://www.virtualbox.org/manual/ch04.html#sharedfolders](http://www.virtualbox.org/manual/ch04.html#sharedfolders)

Or network the 2 VM's together.

Or put your USB device into the machine and mount it in the server VM.

Take your pick.

---

### Post by spynappels on 2012-02-17
What are you using to create the website? How are you transferring the html files to the server? Are you using SSH, because if you are, scp would be the natural choice...

---

### Post by paulwilson5x on 2012-02-18
ok I have the 2 vm's networked what steps do i need to take now, this is my first experience with linux and i have no clue what im doing :(

---

### Post by paulwilson5x on 2012-02-18
im makin the website from the command line

---

### Post by spynappels on 2012-02-18
Ok, let me see if I've got this correct.

You are creating the HTML files on the server using some text editor (vi, nano, whatever) and you want to transfer the images from your desktop to the server to link to them in the HTML code, right?

In that case you can transfer the images to the server using scp, possibly placing them in a folder called images in the document root of the server. Run the following ina terminal widow on your Desktop machine.

```
scp /path/to/image(s) <server-user>@<server-ip>:/path/to/destination
```

Bear in mind that you'll probably have to copy the files to your home directory on the server by scp and then ssh to the server and use sudo to copy them to the final location somewhere under /var/www

Hope that helps, just as an aside, giving more details in the original questions may help you get more relevant answers more quickly.

---

### Post by paulwilson5x on 2012-02-25
First time user of ubuntu. Running ubuntu desktop 11.10 and server 11.10 in virtual box. Have a folder of images on desktop which I would like to tranfer to server for website. Have vsftpd installed on server. I have no ideas of the commands used to transfer this folder. Any help would be great.

---

### Post by josephmills on 2012-02-25
> **paulwilson5x said:**
> First time user of ubuntu. Running ubuntu desktop 11.10 and server 11.10 in virtual box. Have a folder of images on desktop which I would like to tranfer to server for website. Have vsftpd installed on server. I have no ideas of the commands used to transfer this folder. Any help would be great.

so the 1st thing that I would do is in you virtual box go to settings-->network  and bridge that 
2nd I would in virtual server run a ```
 ifconfig |grep inet | grep addr | awk '/:/ {print $2}'
```
Do you see the onr that is not 127.0.0.1 
you want the other one 192.ect or 10.ect 

3rd install filezilla  on host computer (not server)
4) open filezilla
5) go to file-->site manager 
6) under HOST enter in the ipaddress of the server (the one from above). port enter 22 . Protocol enter SFTP ssh file transfer . For login type enter NORMAL. User enter your servers username. password enter your servers password. 
7) press connect 
8) on the left side is your host computer on your right side is the server. so left = host right table = server 
9) drag and drop what ever you like to the server where ever you would like it to be. 
10 ) google scp and look at how to transfer that way also here is a link to help you with that [http://ubuntumanual.org/posts/154/copy-files-remotely-using-scp-in-ubuntu](http://ubuntumanual.org/posts/154/copy-files-remotely-using-scp-in-ubuntu) 

But filezilla should do the trick for you. I hope that this helps. Let us know how it goes. 

Ohh and Welcome to UbuntuForums !

---

### Post by elico on 2012-02-25
rsync or scp is the simplest way to do it using command line.

---

### Post by Morbius1 on 2012-02-25
I've been confused all day on people's post so maybe it's just me but:
> Running ubuntu desktop 11.10 and server 11.10 in virtual box. Have a  folder of images on desktop which I would like to tranfer to server for  website.* You are running Ubuntu 11.10 as the host?
* You are running Ubuntu Server as the guest?
* You want to transfer files from the host to the guest?

If the answer is yes to all of the above create a VBox shared folder for that guest. The guest will automatically mount it at **/media/sf_something**

---

### Post by spynappels on 2012-02-26
Whe you asked this question a week ago, did you try the answers you were given then?

[http://ubuntuforums.org/showthread.php?t=1926577&page=2](http://ubuntuforums.org/showthread.php?t=1926577&page=2)

---

### Post by Morbius1 on 2012-02-26
From the post that spynappels referenced above this topic is getting more complex:
> **paulwilson5x said:**
> ok I have the 2 vm's networked what steps  do i need to take now, this is my first experience with linux and i have  no clue what im doing :sad:
> ok sorry, Im  using virtual box on a windows machine. In virtual box I have the ubuntu  desktop and server. The images on the ubuntu desktop are in  /home/images.The moderators should merge these 2 threads so people who attempt to answer it can get a complete picture of what's being asked in context of the OP's environment.

---

### Post by CharlesA on 2012-02-26
> **Morbius1 said:**
> 
The moderators should merge these 2 threads so people who attempt to answer it can get a complete picture of what's being asked in context of the OP's environment.

Threads have been merged. :)

---

