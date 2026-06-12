---
title: "Ubuntu audio setup"
date: 2010-09-15
forum: Ubuntu Studio
---

### Post by foxruns on 2010-09-15
I've been working to get an audio setup just how i like it and that comes from what Ive used previously fruity loops and sonar, though I'm sure this setup is similar to many others  The main things I wanted to obtain were vst effects and instruments..In the following I will list the programs I use and what I do for a solid audio setup with collaborative programs
This is my first tutorial so questions and any contributions are more than welcome  
I've gotten so much out of these forums i figured I should try to contribute something 
 
  
  
  
 



-Audio Setup and VSTs- 
 	-The basis of the setup lies in Ardour, which if you don't already have can be found in your distributions package manager. Ardour is setup like most other daws and is very easy to learn. It has its own forum, [http://ardour.org/forums](http://ardour.org/forums), and between that and here, you should be able to find all the help you need, make sure to research before you post a thread because chances are someone else has had the same problem. 
 	-Even more important to your audio setup is Jack, jack basically gets your sound to ardour. You will need to set it up with your hardware, being that it is different for every type of hardware I'd advise to search your hardware or just to do some tweaking in jack. To get a visual idea of what jack does follow the next step 
 	-Patchage, also found in your package manager..Patchage is a great way to see everything thats going on in your computer, and though it may seem confusing at first understanding it will help you with your audio setup a great deal. Different types of feed show up as different colors, green is midi through, red is midi in and out and blue is audio in and out, ins will touch the right and outs will touch the left, so only an in can connect to an out don't try to connect an in to an in...for now don't change anything everything will connect to what it needs itself 
 	-The next program is for vst plug-ins, festige which should also be in your package manager, it's a vst loader. I use it for instruments and effects. I use this program because it allows you to use a broader range of vsts instead of worrying about if the ardourvst build will support the vst or not, i have heard it doesn't support as many as festige; also because it allows the use of vst instruments which i haven't been able to figure out in ardourvst build. 
  
 

-VST effects can be found free all over the place..on Google search free vst and you'll get a million results, you can find almost every kind of effect or instrument you want.  
 [http://www.audiomastermind.com/browse-free_vst_plugins-5886988-1.html](http://www.audiomastermind.com/browse-free_vst_plugins-5886988-1.html) 
 i recommend this site^ 
 and this set of plugins as well- 
 [http://www.gvst.co.uk/packages.htm](http://www.gvst.co.uk/packages.htm) 
 after you download you will need to extract the plug-in from the zip file and place it in a folder for all your vsts, its a good idea to make this in your home folder and name it 'vst' or something. if the plug-in is an exe file it wont work..some may work if you have a nice wine setup, but for the most part it is a good idea to avoid plugins that are .exe because they are for windows, you want.dll. 
  
 
	
-Once you have your jack configured and have recording and playback working with ardour open up patchage and festige. In festige find your folder and you should see your plugins, double click to load one, loaded it is not automatically connected to anything, this is where you start to get hands on in patchage. With an effect you want to disconnect the channel you want from its destination and re route its source to the vst, from there you want to route the vst's out to where the channel was originally connected. I will Explain instruments in the next section. You can route effects from audio tracks and busses. If you haven't figured it out already you can move things around in patchage to make it easier to work with and less crowded. 
  
 

 -Midi setup-
-I've had good luck with midi.. i have an m-audio usb audio/midi interface and an m-audio usb midi controller, both of which worked without a hitch. 
 	-The first thing you want to do after you have everything open is open up the terminal and run 
 ```
a2jmidid -e
```  
 if it isn't installed you'll need to install it. After this your midi ins and outs should show up, I've never had any trouble with this as it will vary in effectiveness with every device, so work with forums and Google to get yours working if it doesn't right away. 
 	-after i have my midi ins and outs showing i can start connecting, after opening a vst, connect your midi controller to the vst's in by dragging, then connect your vst's output to an audio in in ardour. If you open a vst and it doesn't show up make sure to try refreshing patchage. 
  
  
 



Thanks for reading guys, any feedback is cool, i hope i helped a few people 
 -fox

---

### Post by Pablo_F on 2010-09-16
> green is midi through, red is midi in and out

No. Green is alsa midi, red is jack midi. This corresponds to the "ALSA" and "MIDI" tabs respectively, in the connection window of qjackctl (aka Jack Control). They are different midi implementations. jack midi is more recent and it is used by some synths and sequencers. You need a2jmidid when you want to connect an alsa midi port to a jack midi port.  You don't want it to connect alsa midi in/out ports.

Yes, Windows VST is possible in Linux, but Linux has its own plugin standards (Linux VST, dssi, ladspa, LV2) with plugins that you can also enjoy. 

Thanks for sharing your experience. 

Pablo

---

### Post by foxruns on 2010-09-16
thanks for sharing your more intelligent experience Pablo :)

---

### Post by phredbull on 2010-11-25
Did you just install Jack on top of Alsa/Pulseaudio, or did you remove Pulseaudio?

---

