---
title: "xbox live vision camera"
date: 2009-03-18
forum: Ubuntu Studio
---

### Post by mikedmor on 2009-03-18
I have a xbox live vision camera and everything is installed using mjpg_streamer. and the tutorial from this site: [http://www.liamm.com/tech/xbox-live-vision-camera-in-ubuntu](http://www.liamm.com/tech/xbox-live-vision-camera-in-ubuntu)

I am required to run this command:
```

mjpg_streamer -i "input_uvc.so -d /dev/video0 -f 15 -r 640x480" -o "output_http.so -p 8080 -w ./"
```

in order to start the cam.

Problem is that when i type "$ ls /dev | grep video" in terminal i will get "Video0" but when i open cheese no video. I added two pictures that show my preferences and what im getting instead of a cam feed.

If you need any other information let me know.

Thanks
-Mike

Edit: sorry if this is the wrong place to post about this.

---

### Post by PorchSong on 2009-04-26
try this command in terminal:

```
sudo modprobe uvcvideo
```

Then fire up cheese, skype or whatever and video will be there.  

The trick is that you have to run that command with each reboot.  But, it does work.

I have to this with I did my fresh install of 9.04.  Only workaround that works and is quick.  Also, I installed camera monitor -- it is a tray indicator that your webcam is on (although the green ring should be sufficient).

---

