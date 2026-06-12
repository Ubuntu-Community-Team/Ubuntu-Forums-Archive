---
title: "HOWTO: Automatic photo upload to Flickr from folder"
date: 2010-02-26
forum: Tutorials
---

### Post by skooter on 2010-02-26
Update 25/04-2010: Error fixed: "unexpected end of file"
Update 21/03-2010: Added scaling before upload

I was looking for a way to upload my photos to [flickr.com]("http://flickr.com") just by putting the photos into a specific folder, but was not able to find any working solution. So I made a shell script to do this for me. For this to work I'm using a [perl command line uploader]("http://search.cpan.org/~cpb/Flickr-Upload/flickr_upload") (which I'm not the author of).


In the end you will have five folders:
[LIST]
[*]"private" - photos only viewable by you
[*]"friend" - photos only viewable by friends
[*]"family" - photos only viewable by friends and family
[*]"public" - photos viewable by everybody
[*]"uploaded" - photos will be moved here after upload (I prefer to move the photos instead of deleting them)
[/LIST]


Here goes:

1 ) Create an account at [flickr.com]("http://flickr.com") (if you haven't got one already)

2 ) Install libflickr-api-perl and ImageMagick
```
sudo apt-get install libflickr-api-perl imagemagick
```

3 ) Download the flickr command line uploader:
[http://search.cpan.org/~cpb/Flickr-Upload/flickr_upload]("http://search.cpan.org/~cpb/Flickr-Upload/flickr_upload")

4 ) Uncompress the downloaded file
```
tar zxvf flickr-upload.tar.gz
```

5 ) Jump into the uncompressed folder
```
cd flickr-upload
```

6 ) Run Makefile.PL
```
perl Makefile.PL
```

7 ) Run make command
```
make
```

8 ) Check for errors
```
make test
```

9 ) Install the uploader
```
sudo make install
```

From here you can only continue if the install went well.

10 ) Run the command and follow the instructions by copying the URL into your browser
```
flickr_upload --auth
```

You will be sendt to Flickr's website and asked to login and agree that Flickr::Upload can access your account.

11 ) After you have finished the wizard on the website press Enter on the command line and a token will show up.

12 ) Copy and paste the token into a new file ".flickrrc" located in your home folder. Open/create file
```
nano ~/.flickrrc
```
Put this into the file
```

auth_token=<your-token-here>
is_public=0
is_friend=1
is_family=1

```

You can now test if the uploader works by running the command
```
flickr_upload your-image.jpg
```

13 ) Now decide the location of the upload-folder. I'll presume that you will use your home folder. Jump to the folder (if you are not already there)
```
cd ~/
```

14 ) We will call the upload-folder "flickr" and create some sub-folders inside
```
mkdir flickr flickr/private flickr/family flickr/friend flickr/public flickr/uploaded
```

15 ) Download the file attached to this thread and save it as flickr.sh inside the flickr-folder.

Before you continue check if the shell-script works. Do this my placing an image in the "private"-folder. Next run the command to start upload
```
bash ~/flickr/flickr.sh
```
The terminal should tell if the image is getting uploaded. Also go to flickr.com an check your photostream.

16 ) Now we will create a periodic job to make the upload happen
```
crontab -e
```

Your crontab should look something like this
```
# m h  dom mon dow   command
*/5 * * * * $HOME/flickr/flickr.sh
```
This will call the script every 5 minut.


That's about it. You are ready to upload photos. Oh yeah and do tell if this was useful :)

---

### Post by Jeeevs2001 on 2010-04-25
At last!! This is exactly what I have been looking for. 

Thank you for putting all this together in a way that even I can follow :-) 

Unfortunately I am getting as error when i try to run the script:

line 129: syntax error: unexpected end of file

I'm sure this is simple to solve so sorry for the newbie question!

---

### Post by skooter on 2010-04-25
Sorry about that Jeeevs. Should be fixed now. Somehow I got it save in a non-unix system (no names) before uploading it. My bad.

I'm really glad you liked the article and that it was understandable :)

---

### Post by icemusike on 2010-04-26
nice tutorial tanks mate. :) realy interesting i didnt know i can do that

---

### Post by skooter on 2010-04-29
No problemo ;)

---

### Post by Jeeevs2001 on 2010-05-23
If your using the upload script on its own you can also install term::progressbar. This will give you a progress bar as your files are uploaded. 

```
sudo apt-get install libterm-progressbar-perl 
```

then just add --progress to the fickr_upload command to show live progress.

```
flickr_upload --progress your-image.jpg
```

Obviously this isn't required with the flickr.sh script, but I thought people might find it useful! 

Thanks again skooter for putting this together. 

Jeeves

---

### Post by kinoauei on 2011-05-02
Hey!! Nice tutorials. Thanks

---

### Post by Frylund on 2012-04-17
Great script, thanks a lot!!!

---

### Post by MeneM on 2012-04-30
The best most stable option so far! and I've tried them all! flickrfs looked promising.. But way to old, and not maintained anymore.

But something like this needs no maintenance. Perfect.

Is there a way to upload using sets? Something like : make the directory you put in "public" the set name?

---

### Post by berggren on 2012-05-12
Thanks!
I'll be testing it.

---

### Post by gubach on 2013-01-18
Has someone made  a script version without the scaling? Thanks!

---

### Post by hyunjaezun on 2013-11-13
Thanks so much, this is almost perfect!!! So it uploads my pictures  silently in the background one by one on my flickr account by just  putting my pictures in one of those folders.

Does anybody have a  suggestion how to command the script to search and include all the  subfolders with its content of: "family", i.ex. :

family/folder_1/sub_folder_1
family/folder_1/sub_folder_2

?

Thanks in advance

---

### Post by Sathesh on 2014-07-15
This does not work. After I click the URL generated for login, the flickr says the following error,
                        	**Oops! Flickr can't find a valid callback URL.**

---

### Post by ben-fluidlogic on 2014-10-19
The Flickr API is now SSL-only - see [http://code.flickr.net/2014/04/30/flickr-api-going-ssl-only-on-june-27th-2014/](http://code.flickr.net/2014/04/30/flickr-api-going-ssl-only-on-june-27th-2014/). This breaks countless unmaintained Flickr utilities. Modifying /usr/local/bin/flickr_upload to change the URI scheme from HTTP to HTTPS didn't fix it; it hangs at "Waiting for upload results (ctrl-C if you don't care)..."

---

