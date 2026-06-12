---
title: "Linux Voice Recognition that really works with your usb mic:) !!! :)"
date: 2012-08-30
forum: The Cafe
---

### Post by patrick295767 on 2012-08-30
Hi,

Having quite some experience with Voice recognition, I am glad to share to you a development, that really shows outstanding results compared to the past dvlpts for Linux in the field of voice recognition.:-) 8-)

Here is my script. You just have to paste it into vim/nano/gedit... and test it. 

voicerecolinux.sh
```


#!/bin/sh


ProcFestival() {
  if [ "$1" = "--festival" ]   ; then 
    echo "$2" | festival --tts
  fi
}

ProcIncreaseMic() {
  amixer -q -c $VALMIC   set 'Mic',1 100%
  amixer -q -c $VALMIC   set 'Mic',0 100%
}

ProcMic() {
  if  [ "$1" = "--checkmic" ] ||  [ "$1" = "--mic" ]  ||  [ "$1" = "--hwmic" ] ; then
    CARDNBR=` arecord -l | grep "^card "  | sed 's/://g' | awk ' { print $2 }  '  `
    [ "$2" = "--debug" ] && echo "$CARDNBR"
    if [ "$1" = "--mic"  ] ||  [ "$1" = "--checkmic"  ] ; then 
      [ "$2" != "" ]  && CHMIC=` echo "$CARDNBR" | grep $2  ` 
      if [ "$CHMIC" = "" ] ; then 
        VALMIC=` echo "$CARDNBR" | tail -n 1 `
        ProcIncreaseMic
        echo "$VALMIC"
      else
        VALMIC="$2"
        ProcIncreaseMic
        echo "$VALMIC"
      fi
    fi 
  fi
}

if [ "$1" = "custom" ] ; then 
  mkdir -p $HOME/tmp/custom 
  wget http://pastebin.ca/raw/2199967  -O $HOME/tmp/custom/sample.dfa
  wget http://pastebin.ca/raw/2199968 -O $HOME/tmp/custom/sample.dict
  wget http://pastebin.ca/raw/2199969 -O $HOME/tmp/julian-custom.jconf
  echo "Custom fetched and done"
  exit
fi

if [ "$1" = "install" ] ; then 
  mkdir -p $HOME/tmp/ 
  cd $HOME/tmp 
  if [ ! -f  Julius-3.5.2-Quickstart-Linux_AcousticModel-2011-07-21.tgz ] ; then
    wget http://www.repository.voxforge1.org/downloads/Nightly_Builds/AcousticModel-2011-07-21/Julius-3.5.2-Quickstart-Linux_AcousticModel-2011-07-21.tgz  -O  Julius-3.5.2-Quickstart-Linux_AcousticModel-2011-07-21.tgz
  fi 
  tar xvpfz Julius-3.5.2-Quickstart-Linux_AcousticModel-2011-07-21.tgz 
  echo "It might be installed."
  exit
fi


if [ "$1" = "voc" ] ; then 
  cd 
  cd tmp
  cd bin
  vim sample.voca
  ./mkdfa.pl sample
  exit
fi


FETCHMIC=` ProcMic --mic "$2"  `
echo "Fetchmic : $FETCHMIC"
AUDIODEV=` echo  "/dev/dsp${FETCHMIC}" | awk ' {gsub("dsp0","dsp") ; print $0  }   '`
export AUDIODEV ;  echo  $AUDIODEV  
counter=1

cd
cd  tmp

if  [ ! -f julian-custom.jconf ] ; then 
  echo "custom/julian.jconf not found"
  echo "Please run-it with custom or install"
  exit
fi


./julian -demo -input mic -C julian-custom.jconf | while read -r  i ; do 

if [ $counter -eq 130 ] || [ $counter -eq 129 ] ; then
  echo "** READY * Please Speak **"
fi

if [ $counter -ge 129 ] ; then
  echo "**$counter** $i **"


  CHPAS=` echo "$i" | grep "sentence1: <s>" `
  echo "CHPAS $CHPAS" 
  if [ "$CHPAS" != ""  ]  ; then 
    echo "FOUND CHPAS $CHPAS" 
    FOUND=""
    FOUND=`echo "$i" | awk ' { print $3  }    '`
    ProcFestival --festival "$FOUND"


    if [ "$LAST" != "ZERO" ]   &&  [ "$FOUND" = "ZERO" ]   ; then 
      ProcFestival --festival "The Command is $FOUND"

      # here add whatever you would like linux to do ...
      [ "$LAST" = "ONE" ]   && xterm &
      [ "$LAST" = "TWO" ]   && audacious &
      [ "$LAST" = "THREE" ]   && xclock &
      [ "$LAST" = "NINE" ]   && date | festival  --tts &
      # ...
    fi
    LAST="$FOUND"
  fi 
fi

counter=$(( $counter +1))
done






```

you can run it with the command in the console: 

Procedure to install:
```

sh voicerecolinux.sh  install
sh voicerecolinux.sh  custom
 
```

Procedure to reco. and play the word:
```

sh voicerecolinux.sh  
 
```

 You might try. =D>


[B]I have added few commands:

if you say ONE then ZERO: it will start xterm
if you say two then ZERO: it will start audacious
if you say Three then ZERO: it will start xclock
if you say NINE then ZERO: it will tell you the time[/B]


If you believe that it sucks, well, you should have tried alternatives on Linux some 10-15 years ago.:-?:roll: Such quality of the reco was not close to be.](*,)

I hope that you might appreciate this tool. Useful for controlling your PC over the voice, since it offers a command line based possibility.

):P  \\:D/

---

### Post by Rodney9 on 2012-08-31
Would be great for disabled persons, however I get this -

```
sh voicerecolinux.sh  --test
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ls: cannot access /dev/dsp*: No such file or directory
```

Rodney

---

### Post by patrick295767 on 2012-08-31
> **Rodney9 said:**
> Would be great for disabled persons, however I get this -

```
sh voicerecolinux.sh  --test
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ls: cannot access /dev/dsp*: No such file or directory
```

Rodney

Hi,

Sorry that my code has not an better dialog thing to make it work more easily. I am too tired to make a nice frontend with dialog

So, let's make it with posts. It looks like that you have a Intel sound card. However you have analog devices. It works, but you might need a mic. It sounds however that you /dev/dsp is missing... for some reasons. 

I would recommend to plug a regular webcam (that has a mic on it). I have several logitechs, and they all have video0 and a mic on it. They are sufficiently good for some voice reco.


The command to type is this one: 
```
sh voicerecolinux.sh  -test
```


Edit : 
PLease check the newer version :)

---

### Post by patrick295767 on 2012-09-01
I have made today a much better script. 

It allows you to recognize and play words such as : 

one, two, ... nine
zero is to validate the word or command

This script also is detecting your usb mic (probable assessment).


[B]I have added few commands:

if you say ONE then ZERO: it will start xterm
if you say two then ZERO: it will start audacious
if you say Three then ZERO: it will start xclock
if you say NINE then ZERO: it will tell you the time[/B]

     

IT WORKS PRETTY WELL NOW !
ENJOY !!

---

### Post by gbrowning on 2012-11-12
I am having trouble getting started with Julius.  Is there a tutorial or How To for completely stupid people somewhere?  I am adding the following--
Dug deeper into the voxforge site and have found tutorials there and in the documents included in the downloads----

---

