---
title: "How To Install And Set Up DOSBox With A Graphical Front End The Easy Way"
date: 2014-12-24
forum: Tutorials
---

### Post by Stephen_Mohos on 2014-12-24
I know there is a tutorial out there for this but this one involves a script that automates the process.

For the do-it-yourselfers out there, there are various tutorials you can follow, but this is for the rest of us.

Just copy the following script and paste it into a text file in your home directory.  Call it whatever you want, I call it SetupDOSBox.  After that click on the save icon to save the file.



#!bin/bash
RecordMidi(){
    MIDI=$6
}
sudo apt-get install dosbox pmidi timidity fluid-soundfont-gm fluid-soundfont-gs
sudo apt-get install openjdk-7-jre openjdk-7-jdk oracle-java7-installer icedtea-plugin default-jdk
dosbox -c exit
cp /etc/timidity/timidity.cfg .
Check=$(grep -c 'soundfont /usr/share/sounds/sf2/FluidR3_GM.sf2/' timidity.cfg)
if [[ $Check -eq 0 ]]
then
    echo 'soundfont /usr/share/sounds/sf2/FluidR3_GM.sf2/' >> timidity.cfg
fi
sudo mv timidity.cfg /etc/timidity
MIDI=$(pmidi -l)
RecordMidi $MIDI
sed -i 's/mididevice=default/mididevice=alsa/g' ~/.dosbox/dosbox-*.conf
sed -i 's/midiconfig=.*/midiconfig='"$MIDI"'/g' ~/.dosbox/dosbox-*.conf
sudo /etc/init.d/timidity restart -q
wget -rnd -A_generic.tar.gz 'http://members.quicknet.nl/blankendaalr/dbgl/download'
sudo tar -xzvf dbgl*.tar.gz -C ~/.dosbox
cp /usr/share/applications/dosbox.desktop .
sed -i '/Exec=/d' dosbox.desktop
echo 'Exec='$HOME'/.dosbox/dbgl' >> dosbox.desktop
sudo mv dosbox.desktop /usr/share/applications
sudo rm dbgl*.tar.gz



Now, type "bash SetupDOSBox" (or substitute SetupDOSBox for whatever you called the text file) in a terminal.

After the script completes its tasks, just click on the DOSBox icon to start the DOSBox front end.

When this script is complete required dependencies will be installed, DOSBox will be downloaded and set up to use MIDI for music playback, Timidity will be configured, the latest version of a front end for DOSBox will be installed and the menu entry for DOSBox will point to the front end.  You did not have to go through a long list of steps to set this up.

---

