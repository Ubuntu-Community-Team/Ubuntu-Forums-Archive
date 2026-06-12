---
title: "Webcam not working; can't view videos, update mgr. ?"
date: 2011-08-06
forum: System76 Support
---

### Post by hkarl629 on 2011-08-06
My Serval (Serp 2) was purchased in 2007. I since doubled the memory to 2Gb. Had a problem with the webcam at that time (2007). Otherwise the computer has been a great one. Am running Ubuntu 10.04. That's  the background.

Now to the problems:

1. Webcam does not work in Skype. I reinstalled the Cheese program and the webcam works there so the problem is not the webcam itself.

2. I cannot view videos such as UTube or those on the financial site of Morningstar.  Often there are flashing windows where the video should be running and I see something about a debugger running or an error occurred and video could not be seen. I did download the Flasher player plugin for Firefox.

3. Strange stuff with the Update Manager. When I see the notification at the bottom of the screen I then close all windows prior to clicking on the Update Manager.  I am getting a window that tells me not all updates may take place. I got one that said to try again, the problem may correct itself, and it did.  Other times no such luck.

Help, please.  I'm doing a presentation on Linux/Ubuntu Aug 12 before a Windows/Mac group. I'll be the odd man out and want to make as good an impression as Ican.

Thanks for yoou assistance.

Henry

---

### Post by hkarl629 on 2011-08-09
With 83 viewers so for and no suggestion, I really do have some problems.

Henry

---

### Post by isantop on 2011-08-11
Hi Henry.

Check the setting in Skype. I don't have a SerP2 to test with, so I can't send you specific settings, but make sure that Skype is set up to use the webcam, and that you have the proper webcam device selected. Also, make sure you aren't browsing on any websites that use flash, and flash can grab the webcam; only one application can use the webcam at a time.

For update manager, co ahead and click cancel on that window, then click the Check button. Let that finish and see id that fixes the problem. If not, I'll need to know which version of Ubuntu you're running.

The Firefox issue has to do with a bad interaction between Firefox's rendering engine (Gecko) and Flash. Unfortunately, I haven't been able to find a solution, but as a workaround, you can use Chromium instead, which uses the WebKit rendering engine instead of Gecko. You can install Chromium from the Ubuntu Software Center, or from the terminal as the "chromium-browser" package (the "chromium" package is a game).

---

