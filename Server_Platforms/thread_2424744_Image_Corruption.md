---
title: "Image Corruption"
date: 2019-08-13
forum: Server Platforms
---

### Post by computeraudio on 2019-08-13
Hello,

I have a new install of Ubuntu server 18.04. This server is just to serve a image slideshow on a web browser.  When I started the apache server and the PHP script, any images in the folder that are bigger then 200kb only load part of the image then the rest of the image is blank.  Thinking it was part of the PHP script or someting in Apache, I browsed to the picture folder from Chrome.  When I clicked on the images, I only got part of the image as well.  If I sftp to the linux server, I get the full picture.  So, I know the image is not corrupted.  This only happens when I open the images from a web browser.  Since it's not specific to Apache, I don't know what log to look for.  Has anyone seen this before?  Thank you.

---

### Post by TheFu on 2019-08-14
check the resolutions for each image.

---

### Post by computeraudio on 2019-08-14
Thank you for the reply.  I did some testing in Photoshop.  I brought the resolution down to 600 x 450 @ 72DPI.  More of the image loaded, but there were still digital artifacts in the image.  Then I brought the jpeg compression down to make the image size smaller, it loaded fine once I got under 150KB.  It seems like this is a problem with the file size.

---

### Post by TheFu on 2019-08-14
For web publishing of images, I generally use a batch solution:
```
#!/bin/bash
QUAL=40
for img in "$@"; do
  NEW=${img/%.???/-opt.jpg}
  echo " Working on $img ..."
   convert -quality $QUAL  "$img"  "$NEW"
done
echo "rename 's/-opt.jpg/.jpg/g' "
```

You'll need **convert** and **rename** tools, though it doesn't rename the new image files as scripted above. Convert is part of imageMagick suite.  Tweak the QUAL setting to your needs.

Also, the image files can't have spaces in the names and funny characters could cause problems.

Photoshop ... ewwww. I feel dirty. ;)

---

### Post by computeraudio on 2019-08-15
The thing that's confusing me about this is that I have an older system based on ubuntu 14 and Apache 2.4.7.  The images show fine on that system both directly loaded in the browser and with my PHP script.  That's why I'm thinking it's an Apache setting or something.  I just don't know where to look for that.

---

### Post by TheFu on 2019-08-15
Could be a php.ini setting too. Or a proxy or security setting for mod_proxy or mod_security.  I don't use php or apache enough to help. Sorry.  

A better title for this thread would have been "Php file download size limits on Ubuntu 18.04"
You want people familiar with websites and php and Ubuntu 18.04. Apache would probably be assumed, titles that are too long cut off the endings from view.

Out of those, I'm only familiar with websites.

Image Corruption sounds like a bad HDD or a desktop problem, which isn't likely to get the experts you want.

Apache settings are always under /etc/ somewhere.  That's a distro thing, if the distro uses some sort of package manager. I'd use **fgrep** to search all the files in the apache settings directory structure for limit or size stuff.

---

### Post by LHammonds on 2019-08-16
Apache default settings (at least for all versions of Ubuntu) allows for 8 MB files to be uploaded.  I am not aware of a download limitation.  Every image on my site, including large ones will display in any browser I test.

If you want to modify the upload size to be 2048 MB, this is how:

```
sudo vi /etc/php/7.2/apache2/php.ini
```

Find and modify these values:
```
post_max_size = 2058M
upload_max_filesize = 2048M
```

Then reload the settings:
```
systemctl reload apache2
```

Are your images actually corrupt on the server?  Did your upload/copy process corrupt them?  How exactly are you uploading them?

How are you displaying them to the browser.  You mention PHP but the code that actually displays images is HTML such as:
```
<img src="myfile.jpg" />
```

LHammonds

---

### Post by TheFu on 2019-08-16
I read that some browsers have issues with some image files. Try different browsers, perhaps there is a clear issue with 1 or 2 of them, but all the others work fine.  I like dillo. It is small, VERY fast and doesn't support things I consider dangerous.

---

### Post by computeraudio on 2019-08-16
Thank you guy for your help so far.  LHammons, I have the images on a Windows NTFS drive and am using cifs to mount the remote folder.  When I SFTP to the server and download the image, they load fine.  On the browser, I'm going to [http://server/images](http://server/images) folder/image.jpg and that doesn't load the whole image either.  For PHP, it generates a <img src="myfile.jpg" />.

---

### Post by TheFu on 2019-08-16
Spaces in directories or files can cause unexpected issues if a programmer didn't quote the entire name in every place it is used.
Old-time Unix guys know to avoid spaces and funny characters in directories and filenames.

I'd check the apache logs to see exactly which files are being served.

---

### Post by computeraudio on 2019-08-16
Ha, I found it.  I was using an older smb version in my fstab file specifying the folder that the images were in.  Once I fixed that and cleared my caches, the pictures now load fine.  The php script works as well.  Thank you guys for the help.

---

### Post by TheFu on 2019-08-16
> **computeraudio said:**
> Ha, I found it.  I was using an older smb version in my fstab file specifying the folder that the images were in.  Once I fixed that and cleared my caches, the pictures now load fine.  The php script works as well.  Thank you guys for the help.

**Everyone** has made a similar mistake.  Different brains are helpful. ;)   

Glad we were able to help you figure it out by triggering something in your mind. YOU figured it out.

Please help the community by using the "thread tools" button near the top and marking it "SOLVED" so others searching will find it and people wanting to help skip it.

---

### Post by techzie on 2019-09-03
For More Information Regarding Proxy You Can visit [192.168.1.2 IP]("https://techzila.net/192-168-1-2-ip-admin-login/")

---

