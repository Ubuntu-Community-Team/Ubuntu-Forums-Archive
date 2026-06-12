---
title: "How do i install VST plugins in Reaper?"
date: 2010-01-08
forum: Ubuntu Studio
---

### Post by JohneG on 2010-01-08
I have Reaper working through wine but i don't know how to or where to install VST plugins to. Anyone able to help me out? Thanks

---

### Post by thorgal on 2010-01-08
just a suggestion:

```

mkdir -p $HOME/.wine/drive_c/Program\ Files/Steinberg/VstPlugins

```

put all your VST dlls in there.

---

### Post by sgx on 2010-01-09
> **JohneG said:**
> I have Reaper working through wine but i don't know how to or where to install VST plugins to. Anyone able to help me out? Thanks

To setup for these (and other) virtual instruments, you also need to create these 2 folders in
 C:\Program Files:  (modify to to your path:

/home/user/.wine/drive_c/Program Files/Steinberg/VstPlugins )

Steinberg\VstPlugins

Put some synths in the VstPlugins folder, unarchived, just drag and drop each single .dll file,

Open the Reaper Preferences panel, (press Ctrl p)

click the VST buttom (near-bottom-left), then, in the upper-right of that panel, click the Add button, and in the browser that appears, browse to

 C:\Program Files\Steinberg\Vstplugins  (or just type that in the space provided)

Then press the button 'Clear cache and rescan directory'. This is how Reaper finds and analyses your virtual instruments.  Ignore any errors messages during the rescan, just click them away. Next, in the main menu, choose

File -> New project  (this removes any loaded project, clean slate)

and choose the menu

Track -> Insert virtual instrument on new track

This opens a browser where you choose an instrument, or effect.  Pick a synth.
When an instrument opens, it will be 'undocked', in front of the Reaper interface, We'll change this in a bit, for now, look at the 3 long rectangle text bars atop the instrument gui

Comment
Preset
instrument default preset 

-the first two will be blank, ignore them. The third one down, will contain the name of the first sound in the soundbank, it is where you click to choose among preset sounds provided with each instrument. The list pops up when you click here. 
To play the sounds:

Now, in the Reaper preferences panel  ctrl p     yet again, choose

MIDI Devices

if you have a midi keyboard connected to your computer, select your midi input keyboard device. If you have none, there is an onscreen midi keyboard for you to use, press alt b ...and click the mouse on the keys, or use the qwerty computer keyboard to play notes. This keyboard is resizeable, right-click in either far side to adjust octaves. Some instruments have their own keyboard which can be used at least with the mouse.

You will see an empty white square at the bottom-right of the instruments interface page, with the word Add in the lower left. Right-click in this empty square, and a menu appears, so near the bottom of the menu, choose 'Dock FX window in Docker', with a checkmark, to dock/undock instruments, and make room for more. (when multiple instruments are loaded, press the FX button in each track, to go to that particular instrument).

You'll notice on the main Reaper interface, the track that was created for your first instrument.

1 the speaker icon must be white or green to monitor your intrument, and the AR button arms the track for recording. Bright red when armed.
2 the i/o icon -if you place a reverb or other effect in other tracks, click the io button and you can add a 'receive' or 'send', to or from other tracks, like invisible patch cables.
3 the FX icon, if you insert an empty track, click this to open the plugin browser. Right and left clicks offer different options on many buttons, so its good to take notes, and peruse the PDF manual found on the Reaper website, which has a fine forum for new users to get elusive answers.

JEWEL! press ctrl alt b to open a panel to record what you play! Its also in the File menu as

'Save live output to disk (bounce)', here, you can give it a title, set the quality, and press the start
button. Then jam like mad!!! Repeat the key-combo or menu choice to stop recording.  Audition levels etc  start recording, and what you play is what you get!


A ComputerMusic Magazine at Borders, or Barnes&Noble, it comes with a dvd with dozens of fine virtual instruments, a steal at $18.

---

