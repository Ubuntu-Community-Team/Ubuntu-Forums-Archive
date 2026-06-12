---
title: "lm3jo"
date: 2014-02-24
forum: Ubuntu Studio
---

### Post by temps-jo on 2014-02-24
Hello, 
I am the developer of lm3jo 
How to incorporate the package lm3jo.deb in ubuntu studio ?
it is here 
[http://www.letime.net/vocale/paquet_deb/lm3jo.deb](http://www.letime.net/vocale/paquet_deb/lm3jo.deb)

---

### Post by su:bhatta on 2014-02-24
Is lm3jo a synthersizer or a 16 track mixer or both. 

Sorry, but the website: letime.net is not in English so couldn't make much out of it. 
Does it integrate with JACK too? 

Would be very helpful if you could give some site that says what is the use of lm3jo or if you can provide any details.
Thanks

---

### Post by temps-jo on 2014-02-24
Hello, 
Thank you for the reply. 
lm3jo deb is a synthesizer that allows you to write the acoustic hammer with only 3 bytes that produce 100 kb wav  
Acoustic hammer this particular form is found on many sounds, such as piano or guitar. 
This is an audio application that uses no compression, just modeling sounds.
I use sox to make my modeling compatible with the current audio technology. 
I create the possible forms of the acoustic laws using small code in C language
Everything is very light and consumes very few resources 
I am running my techniques on a arduino.
if you look at the speech synthesizer, I do surf sounds of consonants on vowels, using the laws of acoustics that I discovered




   This weekend I wrote a tutorial usage in English .

---

### Post by su:bhatta on 2014-02-25
It would be nice if you provide a link to the tutorial. 

And, does this work with JACK?

---

### Post by temps-jo on 2014-02-25
If jack works with sox, yes 
because I used sox, this until I find a fabliquant sound card according to the plans that I drew (no more sox, no more direct conversion, the signal gives the future to the audio card, it is before the present. 
 the signal sait to component that makes sound where he must go.)

---

### Post by temps-jo on 2014-02-26
How_to_lm3jo

   Lm3jo is written to the 13.10 version derived from ubuntu .
The current address until the ppa is [http://www.letime.net/vocale/paquet_deb/lm3jo.deb](http://www.letime.net/vocale/paquet_deb/lm3jo.deb)
using qapt -deb -installer .

Once installed you need to open a terminal.
During operation lm3jo creates audio files so that designers can retrieve new sounds .
So as not to create audio files in a limited area it is advisable to create a directory and put himself inside
sudo mkdir mySound
cd mySound
To launch the application, you must enter the terminal
lm3jo
Once launched the application opens on a keyboard 78 keys.

1) Virtual piano mode ( Acapela , Flute , Drum , bass, guitar, sax, organ , piano, fun , violin, Guit.Elec . , Nature )

12 buttons at the top allow you to change the sounds behind the keyboard 78 keys keyboard sounds are 936 base.
Sounds can be played on the mouse , and the QWERTY keyboard. The QWERTY keyboard uses the 26 keys at the bottom, it is possible to play several keys simultaneously .
The basic library are under construction and several sounds are still experimental .

2) Fashion joa jo

The joa jo mode is used to easily create the basic library 2704 sounds
Its bases can be shared or used for convenience by each creator.
To create a sound with jo format, click on the button joa jo
You need to open a spreadsheet and creates two columns composed of values &#8203;&#8203;between 30 and 220.
The first value is used to indicate the amplitude of the acoustic front.
The second value is used to indicate the duration of the acoustic front in 1/44100 second.
In the open lm3jo window, click on the first tab and copy / paste the two columns in the text file that opens .
Then you must click on the second tab and name the created audio file .
This name must be composed of two letters susceptible to breakage. In such aA or AA or Aa or AA 4 different sound files.
To finish , you must click on the third tab that creates the file and gives a first listening to his creation.
Warning sounds depend on the physical laws of physiological laws , and what the brain wants to hear ( the understanding) .
For understanding, if we take as an example a human voice and we remove the part of the sounds placed just before a front of large amplitude , the brain will refuse to recognize the human voice and identify likely a piano . Automatic packaging suspected strong is present in acoustics.



3) Mode composition mix

The interchangeable first level library is composed of two sensitive letters ( in example ab , aB , ... Fj ) is 2704 sounds .
First you must click on the mix composition Mode button. The window opens to the right of the opening text files button.
In these text files can associate sounds by creating suites, to take the example : abaBFj
The right button allows reading these text files.
Line 1 is for a track .
Line 2 is 2 tracks the associated line 1 to line 2 , and up to 16 tracks .


4) Playback Mode Text

To open reading text mode , you must click on the button with the same name .
We find in the window that opens only two buttons.
The first button is used to enter the text that you want to listen .
The second button is used to read the text entered .
Currently this feature is under construction on the French language.
It is planned later to add other languages.

5) Mode screen Dna

Dna mode format is one of the best representation format abadie jo
To use it, you must click on the button
With only three bytes we can produce a large number of acoustic hammers .

To open the window you must click on Dna size
Adn the window has 8 buttons for creating, a button to play the audio file created and a button to delete the audio file.

The first button is used to create acoustic hammers.
You must enter 3 values &#8203;&#8203;with none above 220 .
The first to indicate the variation in amplitude .
The second to indicate the change in length
The third to indicate the total duration .
The second button on the same line for write once sound created in the audio file.

The third button is used to create the unicorn.
You must enter values &#8203;&#8203;9 .
The fourth button is used to create the sound created in the audio file

The fifth button is used to create the wedding
You must enter 19 values.
The sixth button is used to create the sound file created in the audio file

The seventh button is used to create the vinaigrette
You must enter values &#8203;&#8203;4 .
The eighth button is used to create the sound created in the audio file

The ninth button is used to listen to the audio file contained

The tenth button is used to delete the audio file contained

bonus Lm3jo
A suite of 50 fronts that can be controlled with sliders .
A cursor power force, a slider forr amplitude and a slider fo duration .



To make it simpler, we can conclude that sounds are compounds vacuum to hear the significant wave fronts. 
Several causes can have the same effect. 
That the same cause has different effects depending on how it is surrounded. 
That sounds are associated with the physical sciences, are assoiated with physiology, and still associated with the laws of the human mind. 
To create sounds we use techniques thoughts of our Gallic ancestors. We can not do it with algebra concepts or frequency. 
cordially

---

### Post by cub on 2014-02-26
> **temps-jo said:**
> Hello, 
I am the developer of lm3jo 
How to incorporate the package lm3jo.deb in ubuntu studio ?
it is here 
[http://www.letime.net/vocale/paquet_deb/lm3jo.deb](http://www.letime.net/vocale/paquet_deb/lm3jo.deb)
You would need to get the application included in the Ubuntu repositories. I'm not sure how that's done exactly but Ubuntu Studio only includes packages and applications that are available in the standard repos.

---

### Post by temps-jo on 2014-02-26
Thank you for the reply. 
I'll wait a little bit, this is only four years since I created this audio format. 
And I have not yet managed to create a ppa 
cordially

---

### Post by su:bhatta on 2014-02-27
Thanks a ton for the details. 
This weekend gonna get hold of the deb and give it a go...

---

### Post by temps-jo on 2014-02-27
Hello, 
the link to the deb sources is :
[http://www.letime.net/vocale/paquet_deb/sources.lm3jo_deb.tar.gz](http://www.letime.net/vocale/paquet_deb/sources.lm3jo_deb.tar.gz)
I have not arranged the position qt, and the most advanced code is the first key of the piano, I have not yet changed the other. 
It should also indent with indent Application
3a.tar.gz have the concept, but sources lm3jo.deb has a better code
This code can be greatly improved for a particular task as required.
I'm good in concepts but much less programming

The code of the unicorn is not finish

cordially

---

### Post by temps-jo on 2014-03-03
Hello, 
I modified the source code, in preparation for a makefile

it is here [URL="http://www.letime.net/vocale/paquet_deb/sources.lm3jo_deb.tar.gz"]http://www.letime.net/vocale/paquet_deb/sources.lm3jo_deb.tar.gz

[/URL]cordially

---

