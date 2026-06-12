---
title: "Is it possible to programatically simulate clicking on a system notification popup?"
date: 2020-09-23
forum: Ubuntu, Linux and OS Chat
---

### Post by rmsylvester on 2020-09-23
Does anyone know if it's possible to simulate a click on a system notification popup type message? (not sure what the correct terminology is) Like one of the ones that gets displayed at the top middle and has a little cross icon, and if you click on it then it opens something up usually?

---

### Post by sdsurfer on 2020-09-23
I don't know the correct answer, but it might be better answered if you provide context, as in, what are you trying to do? I do know that even in web browsers, while it's easy to do something like this within a code set under your control, it's a bit more difficult to do this external to a program. If that were possible, it would be far too easy for spammers to submit forms, OK to things people don't want to OK, etc. (Those are really bad examples because there are ways to do that, hope you ge the idea.)

---

### Post by TheFu on 2020-09-23
Perhaps.  It depends on the programmer of the button you want to click.  **cnee** can send X-events to a specific place on the screen.
cnee can record keyboard and mouse events.  Something like this will start the recording:
```
$ cnee -t 2 -rec --first-last  --keyboard --mouse -o test.xms  -sk q
```
Press "q" to end recording.  Just change the -sk option to change that "end recording" key.  Perhaps F12 would be better?

To replay, use:
```
$ cnee -rep --synchronised-replay  -f  test.xms
```
The xms files are pretty ugly.

xdotool can also do mouse clicks. The hard part is getting the Window ID to send the message. I've had to use multiple other xdotool commands to get that. For example:
```
FF_WINID=$(xdotool getactivewindow)
FF_WIN_LOCATE="window $FF_WINID"
CLICK="mousemove 0 0 mousemove 585 394"; xdotool $FF_WIN_LOCATE  $CLICK click 1
```

I don't know if notifications are real windows. You'd probably have to search each time, since each would have a different ID.

---

