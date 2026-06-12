---
title: "Advice on Audio Characterization in UbuntuStudio"
date: 2012-04-23
forum: Ubuntu Studio
---

### Post by SunPowered on 2012-04-23
Hey everyone,

I am running UbuntuStudio 11.10 with all audio application selected on installation.

I am attempting to configure a complete audio engineering / audio characterisation station and am really hoping Ubuntu Studio will be my one-stop shop for everything I need.

I have successfully configured my M-Audio MobilePre with Jack, and set up my studios for individual tasks (I really like the LadiTray/gladish interface!).  Also, I have a low-cost scope built by Syscomp, to take realtime signal and spectrum analyses.  

I have one last critical task before my dream station is complete.  I require to take THD+N and SNR measurements of the audio amplifiers being designed here.  With my digital scope, I can export a FFT spectrum, and I know I could theoretically process this exported file in scilab or something equivalent to get the measurements that I require.  Before I go and reinvent the wheel (i.e. learn scilab, implement my measurement algorithms, format output, etc)  I figured I would ensure there is nothing out there that could be easily integrated in my setup.  

Is anyone aware of projects out there that can be set up with ubuntu studio to make some more detailed audio quality measurements?  Ideally, I would like the ability to program some scripts to run through tests automatically and report on the results in the format of my choosing.  I am debating whether to forego the scope completely and attempt to do this with the current ubuntu studio tools (i.e. create a 1 kHz waveform and send to amplifier, capture the amplifier output, perform a FFT and subsequent THD+N and SNR measurements in scilab, split out results to a file).  I suppose this could be done, unfortunately however,  I am a physicist, not a computer scientist, and am unsure on the best method of achieving this.  

So in short, does anyone have an idea how to perform audio quality measurements with the ubuntu studio distro?  Searching online,  Baudline ([http://www.baudline.com](http://www.baudline.com)) seems to be not a bad way to visualize and capture these measurements in real-time, yet it is not available in the repository.  

Or ... should I be looking at another distro for these types of precise engineering measurements?  I really hope not :)

Anyway, I appreciate any help you are willing to offer.

---

