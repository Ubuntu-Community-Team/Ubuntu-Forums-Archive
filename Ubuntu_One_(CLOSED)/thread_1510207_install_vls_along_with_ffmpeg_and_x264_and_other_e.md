---
title: "install vls along with ffmpeg and x264 and other encoders"
date: 2010-06-15
forum: Ubuntu One (CLOSED)
---

### Post by chinnaedu on 2010-06-15
Hello all,
i have been working on vlc (windows) and now i want to use the same in linux...so ma trying to compile it in linux..... i need ffmpeg functionality and others as such...so please provide me with the complete link and order  so as where to fetch the source code and to compile....i have done googling and found lots of tutorials and most of the are confusing and not clear......and i tried doing them and am now confused(whether they are compiled or not) cos when i try to instll them it says already exists and when i try to use the functionality it says canot transcode ffmpeg doesnt exitst.....


i am badly need of vlc transcoding options ....so anyone please do guide me with a good tutorial....

Any help is highly appreciated

note: Am using ubuntu 10 now........

Thank you

regards
Harish

---

### Post by Linuxforall on 2010-06-15
Harish, add medibuntu repos if you haven't by now and you will find vlc in it, no need to compile as such. To install ffmpeg and x264 codecs in terminal paste sudo apt-get install ffmpeg libavcodec-extra-52

---

### Post by chinnaedu on 2010-06-15
Thank you for your quick response....

i didnt get wat u meant "add medibuntu repos"

i did this earlier [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)
and as i said confused whether installed cos transcoding with venc=fmpeg and venc=x264 didnt work properly
and also how to uninstall .......?

even that steps too

Thank you

---

### Post by d3v1150m471c on 2010-06-15
```

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
sudo apt-get install vlc ffmpeg libavcodec-extra-52

```

---

### Post by chinnaedu on 2010-06-15
Thank you for the response....am trying the commands....
I will post  O/P after i do.....

ANd how to uninstall it incase if already another insatnce exists....clean it and re-compile...? how

Thank you,

---

### Post by chinnaedu on 2010-06-15
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783


This is the error i received when i ran those two commands,.....

Thank you

---

### Post by chinnaedu on 2010-06-15
then i tried this

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update


now am using transcode option of vlc with venc=ffmpeg and vcodec=h264(gives an error)
 acodec=mp3(which transcodes to mpa(says generic))


and when i give acodec=mp4a(transcodes to mpeg4(says generic))

is it hte correct output.....cos when i play it in mobile it doesnt give me sound....al it does is a hissing sound and video is ok.....

any idea please do reply..

Thank you

---

### Post by d3v1150m471c on 2010-06-15
use ffmpeg instead of transcode or vlc
```

man ffmpeg
# For more straight-foward instructions
info ffmpeg

```

---

### Post by chinnaedu on 2010-06-16
vlc "/home/harish/1.3gp" -vvv input_stream --sout='#duplicate{dst=display, dst="transcode{venc=x264{keyint=2,idrint=2},vcodec=h264,vb=300,width=320,height=240,acodec=mp4a,ab=32,channels=2,samplerate=22050}:rtp{access=tcp,dst=<ip here>,port=15000,sdp=file:///home/harish/1.sdp}"}'



This is how my transcoding command looks like....which generates an sdp file which has transcoded file format thing in it....

and dats why i need ffmpeg,x264 and other encoders if any to be used in vlc (transcode option)

---

### Post by chinnaedu on 2010-06-18
Anyone who knows the answer to the above thread.........?

---

