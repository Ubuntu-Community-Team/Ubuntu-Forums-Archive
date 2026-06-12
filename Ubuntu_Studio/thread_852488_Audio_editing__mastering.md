---
title: "Audio editing / mastering"
date: 2008-07-07
forum: Ubuntu Studio
---

### Post by eArquilla on 2008-07-07
So as to not scare people off with an extremely long post, I'll have a short and long version. Skip the long if time is an issue. Read the long if you want to understand my situation more precisely (and chuckle at an audio newb)

Short:
I need help understanding the theory of music editing AND an example of putting that theory into practice using ubuntustudio apps, most importantly (I think) for my needs: ardour, audacity, and jamin. 

I have basic knowledge of how to connect jack and record in ardour. I don't understand any theory behind music mastering in jamin, what the aim is, how you want the spectrum to look, etc.

Long:
I've had UbuntuStudio installed since it's release, upgrading with each release and to the 64 bit edition. I successfully got my Presonus Firebox working with it. I don't have a single -problem-, more of a question about how to use the software to it's fullest potential.

I think that most of the open-source software developers assume their audience has knowledge of recording, editing, and mastering with closed-source apps. I, however, have just begun.
I'm 19 and have played guitar for quite a few years, however, I have never been in a recording studio or had knowledge on how to correctly edit music.

What I have generally done is create one track in ardour and record from a condenser mic in the middle of my basement. Then my drummer, bassist, and I simply jam.

I moved to Denver for the summer (for a job), thus I'm experimenting on trying to record the way a professional would. So recently, I've been:

Creating 2 mono tracks in ardour, one for rhythm guitar and one for lead. I record each one separately, of course. I then export each track individually and open it in audacity. There I amplify the track to a desired volume (obviously never above 0.0 dbs) and use the noise reduction effect (getting the noise profile from a few seconds of silence). 

After doing this to each track, I export them to a file, open them in ardour, and create a third track for Jamin'. Here is where I really guess. I know how to get Jack to work it's magic and get the tracks into Jamin'. I'll play the whole song through once, make sure the tracks don't go past 0.0 db, and then take note of the highest db of each fequency in the spectrum tab.

I have messed around with the compressor and equalizer settings incessantly, trying to discover myself how to get the music to sound the way I want. So other than, 'do whatever sounds good to you', how should I adjust these settings? I feel like I'm butchering the sound most of the time and usually leave the file the way it was originally. I've read many, many pages of editing theory and such. I ran across one site with recommended compressor settings for different instruments, but it was not for multiband compression, so I was clueless as to how one goes about adjusting the compressors for all three ranges of frequencies.

My technique thus far has been to look at the spectrum, if something seems relatively high, which is usually the high frequencies for the audio's I've been using, I'll set a high threshold for the high frequency compression and set the ratio to 6:1 or so. Using acoustic guitars, the bass is usually very low to non-existent, so I really don't know what to do. I end up setting the threshold to -20 or so and the ratio to 1.2:1. The middle frequencies are generally consistent, so I set that to a -20 threshold and 1.5:1 ratio.

I'm not sure how to throw in the equalizer into this. My guess has been to try to either 'equal' out the spectrum, or make the lows and highs equal with the middle frequencies higher, like a pyramid shape. I understand you adjust as necessary for your own individual taste, but I need a starting point! I have no idea where to begin; i need a median I can later adjust to find my preferences.

Questions:

Is it just common sense that there shouldn't be loud low frequencies on a two track-acoustic?

If a threshold, let's say on the mid, is at -20, is this affecting the mids at any time the entire audio level is above -20, or simply when the mids are above -20? another newb question, i'm assuming it has to be when the entire audio level is above -20, because for my audio's at least no individual frequency goes above -30.

Can Jamin' effectively do what I am doing through audacity (i know it can increase volume output, but what about removing excess noise? is this done with effective compressing?)

Should each track in ardour be mono if I am planning on mastering them to a single track? is there a difference? If I add a drum beat with hydrogen, should that be mono and all three be mastered to a single track?





If anybody can help me with this, or point me in the right direction, please reply. UbuntuStudio seems so powerful and I feel like I was only scratching the surface, and now I'm scratching it the wrong way.

I simply cannot find examples on people taking their tracks and manipulating them with all of these open source apps with detailed descriptions of each step and why they did it. 

Thanks in advance!

---

### Post by eArquilla on 2008-07-07
No idea if this has ever been posted, but this is in the realm of what I was looking for

[http://briansbedroom.blogspot.com/search/label/jamin](http://briansbedroom.blogspot.com/search/label/jamin)

Step by step guide. Haven't read the whole thing yet as I am still at work, but when I get home this is going to help a lot.

Still feel free to give me advice or answer questions, I'm sure this website won't answer every question. But it will help. And something like this should be made much more public to UbuntuStudio beginners. The tutorials for ardour and jamin are a start, but they don't teach you how to start from square one and end with a complete song.

---

### Post by ryanisablond on 2008-07-08
First: congratulations on deciding to go the open source route for music! I wish you luck on your exploring.

As far as your other questions go, I can only offer my experience with general recording/editing theory/application, as my hardware is way too old for music production.

Typically, the process is RECORD -> EDIT/MIX -> MASTER, with lots of listening in between. It sounds like (no pun intended) you're moving straight to mastering to try to get the sound you're looking for. In a perfect world, your mic placement would be so perfect that you wouldn't need to EQ anything. There's lots of theories and opinions on the matter, but what is boils down to is the fact that you just can't boost a frequency that's not there. Moving the mic even a couple inches (or even just rotating it 45 degrees) can have a huge effect on your tone. Google for "common mic techniques" and you'll be overwhelmed with ideas.

I know my recordings are far from perfect, so I often compensate with a little EQ (a little can go a long way). My favorite reference is here: [http://www.digitalprosound.com/2002/03_mar/tutorials/mixing_excerpt1.htm](http://www.digitalprosound.com/2002/03_mar/tutorials/mixing_excerpt1.htm)

It's in the mixing stage that you can craft your tone and dynamics within the song. Generally, the multi-band compressors are more helpful in the mastering stage. Regular compressors are great for controlling your dynamics (although they can easily be waaaaay overdone, just like reveb). Used correctly, compressors will help your tracks "sit well" in the rest of the song, without jumping up or down in volume.

Mastering: there is a reason professionals get paid big bucks here. It's a bunch of little tweaks that take a well mixed song up to the next level. It's not worth skipping to the mastering stage if your mix still needs work. I'm still working on the basics of mastering, so I can't say too much about it. But it looks like briansbedroom has some pretty good resources there for introducing the concepts. The way I've been taught is that it's a gentle EQ/dynamic "massage" to the song to make it sound it's best, bring it up to levels that can compete with other mastered songs, and adds a "cohesiveness" to the feel of an album.


So in a nutshell: record the best possible signal you can. You can fine tune (not create) your tone with EQ (unless you're an electronica artist). Mastering is the icing on the cake: most of the work on is in recording/mixing.

Hope that helps!

---

### Post by thorgal on 2008-07-08
hello,

I am also a self-taught sound engineer and have been exploring quite a lot since I started (about a year ago). I have been playing music for many years and trained my ears a lot, so you should start from there, listen to a LOT of different things to integrate or assimilate the "language" of frequencies. Then, it depends on your audio setup : quality of your micing, monitors (type of speakers, they should be as neutral as possible, no artificial boost in the whole freq range), type of preamps, AD converters, style of music you're composing, etc. 

Now, if you're happy about your sound takes, you have to let them sit well in the mix. If it requires some EQ, use it. You can also remove unecessary frequencies so that you don't overload the low-mid freq area (200 to 800 Hz). This is where most of the human voice sits usually so it's important you don't staurate with other instruments. The compression is to attenuate too large dynamics : if you set up the preamp level of the voice so that you don't clip the loud screaming of your singer, chances are you won't hear much when the singer whispers something between 2 screams. So the compressor will help attenuating the gap. But too much compression can kill the natural feel. Of course you can use the compression for weird effects (like on drum tracks, to make them punchy for example).

Anyway, once your mix is well balanced and you're happy about the whole song, you then master it. The purpose is to boost the overall level to the maximum without distorting the mix or worse, clipping it. If you just have occasional burts above 0 dB, you can use the very efficient fast lookahead limiter jamin comes with. Mastering will make your song shine : you boost the bass, medium, and high freqs and at the end, you dither the whole thing so it sounds consistent and shiny. However, playing around too much with the 3 band compressors can destroy the original feel of the song. So itøs important, when you have a mix that sounds good, to keep it through the mastering process. What you want to achieve is loudness without distorsion. 

Don't do this with headphones or far from neutral environments, you have to get as little bias as possible or your mix will be OK in your room but sound like crap in another place.  

Now, for recipes, there aren't. It all depends on the song you're creating and the vision you have for it. Trust your ears in all this. Apply different mastering and listen to your song in different places. One trick I ended up with relying sometimes (don't laugh) : if despite my high quality gears and hours spent in mixing and mastering, my song soudns like **** on my crappy laptop, then something went wrong. The idea behind is that even on the laptop, which is definitely not a reference in terms of sound quality, my song should shine :)

---

### Post by darenw on 2008-07-08
If you're in Denver and getting to Boulder isn't a big deal, try to hook up with Boulder Digital Arts, a group of producers, artists, musicians etc who hold fun meetings with demos, offer classes.  [http://www.boulderdigitalarts.com/home.asp](http://www.boulderdigitalarts.com/home.asp)   Just chatting with people at get-togethers you  might find good tips where to start and refine your technique.

---

### Post by Bungo Pony on 2008-07-08
> Typically, the process is RECORD -> EDIT/MIX -> MASTER, with lots of listening in between.

I agree that it's essential to get your basic tracks down first. After you've done recording them, throw each one into a wave editor without the other tracks. This is where you'll want to silence anything that shouldn't be there (floors creaking, accidentally hitting the strings, singer clearing his throat). Also, if there's the occasional mistake, you can copy & paste from a point in the song where the part was played correctly. I can't count how many times I've done this! :)

When it comes down to your final mix, the only things you really need a compressor on are the parts that have inconsistent volume (unless you want the inconsistency). Electric guitars and drums usually don't need it. The vocals should heavily rely on compression to bring quiet words back up to the forefront. Acoustic guitars will sound a lot warmer if you put them through a compressor. Personally, I also put my bass guitar through a compressor, but I don't think it's extremely necessary.

The EQ is your friend! If the vocals don't sound full enough, turn up the low end. If the cymbals don't sound sparkly, turn up the high end. If you want something brought out to the forefront, turn up the mid-range. In otherwords, use your ears. Also, be aware of using too much low-end to make your recording "boomy". When people use too much, it distorts and sounds like crap. A good balance of highs, lows, and mids will make your recording sound well-rounded and professional.

Then, add effects as needed. I always like a little bit of reverb and echo on my vocals, but not so much that it sounds like a cheesy 80s recording. Again, drums are usually exempt from effects unless I need to draw out symbal crashes or provide a special effect, such as a distant snare drum. Bass usually recieves nothing as well. Guitars usually recieve the most attention from me when it comes to effects. They're the ones that carry the general sound of the song, and need to sound good. The effect also is meant to fit and / or define the 'style' of the song.

Something that has helped me immensely over the years is to take notice of how modern recording are mixed. How loud is the bass? How are backup vocals mixed? What is that sound that seems to fill in the gaps of the recording (it's probably a synthesizer). What are the little accents that give the recording that unique sound? (could be a marraca or even hand clapping)

Anyway, I wish you good luck in your recording ventures! It's a lot of hard work single-handedly producing your own music, but when you get a great finished product, all the hard work is well worth it!

---

### Post by steevc on 2008-07-09
It's not Linux specific, but Tweakheadz is often recommended as a place to learn recording techniques such as mastering

[http://www.tweakheadz.com/mastering_your_audio.htm](http://www.tweakheadz.com/mastering_your_audio.htm)

The forums include a number of people who do this stuff for a living.

Personally I've got a way to go before I worry about mastering. I'm still getting into basic recording.

---

### Post by eArquilla on 2008-07-09
Thanks for the replies, with your advice and links I was able to fill in many missing pieces in my knowledge of audio editing.

2 final questions - 

1. I was indeed skipping the mixing stage. Looking into this stage, I realized that panning is mentioned a lot. From what I've read, drums should be panned to either the drummer's or audience's perspective. Either way, if using hydrogen, this has to be done in hydrogen before being recorded to ardour, correct? No way to pan a snare one way and kick the other after recorded in ardour, is there? Besides panning, effects are mentioned in mixing. There have been recommendations to try reverb on vocals and some other basic ones. I know very little about ladspa plugins, but I'll mess around with some. Any other important mixing tips?

2. Being a beginner, I wasn't looking to spend too much money on equipment. I got a firebox about a year ago, and I just purchased the M-Audio Studiophile BX8A's. Is this a decent setup? Anything else necessary to add? Firebox has preamps, so I believe I'm set there. Also, I hear the room acoustics makes a big difference. Living in a dorm(I know, the BX8A's are way too much for a dorm room, but I plan to hopefully keep these around for a while), any advice on making the acoustics a bit better? (Obviously small room, one door, cheap tile floor) I'm in a single, so there won't be fuss from an annoying roomate :)

Thanks again for your help guys. With all of this info hopefully I'll have adequate skills after a couple years of practice to go with my setup.

---

### Post by ryanisablond on 2008-07-09
You're right about the drums: panning them around is a very common practice. 

It's easiest to send a stereo feed from Hydrogen into Ardour, most likely using the master output. In that situation, you'd pan the drums first and then record with your kit pre-mixed (performance, dynamics, pan). 

The other option is to send individual outputs from each "track" (i.e. one for snare, one for kick, one for cowbell... can't remember if "track" is the word Hydrogen uses) and send them to discreet tracks in Adrour. This is a little more complicated approach, but gives you the most flexibility in your mixing later. You could add reverb to the snare but not the kick, for example.

I believe there's a howto in the Ardour documentation somewhere. If I can find the link again, I'll post it here.

---

### Post by Bungo Pony on 2008-07-10
Since the drum track is the first thing I record, there is a very good chance that I will return to it and change the volume of some parts of the drum kit. It may sound good as a stand-alone drum beat, but when it's mixed in with other instruments, some parts may get drowned out.

Do a rough mix with your existing drum track and see how it sounds. By rough mix, I mean get the basic elements of the song (drums, guitar, bass, vocals) to the volume you want and play it together. If some part of your drum mix is too quiet (for me it's usually the snare), then go back and change it. Make another rough mix (or re-play the drum track with the fixed part) and see if there's an improvement.

Drums are always the most touchy thing to mix, since it's essentially multiple instruments being played together. Everything else is just a single instrument.

---

### Post by qman_txun on 2008-07-18
Thank all of you for all this posts but I have to be confess that I don't get the idea what to do about mastering. I get all the connection going trough jack and it sounds on the main playback that the effects that I put or change trough the EQ it goes but when I export the audio then I don't get the effects, so I would like some step-by-step toturial how it's done the mastering using ardour+jamin, it could be so nice if there's a little video clift. I'm in Guatemala, I had no class about music nor recording but I have done some recording using audacity and I would like to get great sound and I have learned to record multytrack using ardour, the only piece that I can't get is the mastering with jamin with ardour. I'm very interest in participating in some class if possible, here in guatemala there're but using windows apps which I don't like because I live in a rural area, way to the norwest of Guatemala (Todos Santos, Huehuetenango). I look for some help from you all.

---

### Post by qman_txun on 2008-07-18
What this paragraf mean
"JAmin itself does not have recording capabilaties on it's own so the output of JAmin has to be given back to a recording software, in this case it is Ardour.  _for this we mane Audio 3 track in Ardour as a stereo track_ and give the Left and right outs of Ardour to this track"

Is this mean that I need to make a new audio track and record back what it comes out from Jamin? I hope is true, I'm going to try it and I hope I hear some information from you guys.

---

### Post by thorgal on 2008-07-19
no, you just need to create an insert in ardour's master track post fader area. Right click on this area, select "New insert". Double click on the insert (by default called insert1, you can rename it if you want). You will have a routing dialog window showing up. Now, let yourself guide by the audio signal path to connect the right thing to the right ports :

an insert is a path deviation from the main path that comes back to the main path a bit further, so what you want is to redirect the post fader signal of the master track to jamin, and then from jamin back to the master track. So you connect jamin's inputs to the insert outputs, and jamin's outputs to the insert's inputs. Very easy. Don't forget to disconnect jamin's ouputs from your system outputs in the qjackctl's connection window, otherwise, you will get twice the audio to your system outputs. Once the connection is done, activate the insert (right click on it and select activate).

Now, you can tweak jamin until you're happy and export ardour's session with jamin's effects :)

PS: that's what inserts are for, if you have external dynamic effects you want to patch to a track. Instead of having the track audio signal flowing straight, you insert an FX box on the way to alter the signal. Adding a LADSPA plugin to an ardour track is conceptually an insert but it remains internal to ardour. Whereas using jamin comes down to using an external insert. I hope this makes sense. Just experiment a bit and it will become very clear :)

---

### Post by russo.mic on 2008-07-26
Jesus,  why all the hard and soft rules?  

Look, when recording music, the ONLY rule is does it sound pleasing to you?  Sometimes compressing the hell out of something can sound really cool, really bring out the flavor of the unit your using.  Sometimes theres a need for no compression.  Depends on what you want. 

Compression is one of the most hard to understand tools in a recording engineers arsnel.  I recommend you buy a cheap hardware compressor just for your learning.  I couldn't rave more about the RNC by a company called FMR audio.  ebay that and you'll be shocked by how cheap.  I use them on sessions sometimes over my $1200 spectrasonics comp!  

Forget about mastering right now.  That is a whole other can of worms.  Just make some recordings in ardour that you think sound pleasing to you, and get them as close to unity as you can.  Compare them to comerical records you love, and figure out the difference.  I'm still doing that after 15 years!  and I know personally that you'll always be doing that if recording is a long term goal.  Besides, most recording engineer's don't master there own stuff anyway.  If you have to strap a limiter over the master bus to get it to leve, go for it.  Whatever sounds good.

Sorry for the long post, but I truly love what I do, and love talking about it.  If you want to hear a session I just finished up, that i'm particually proud of, 

[http://www.myspace.com/baakgwai](http://www.myspace.com/baakgwai)

I did the first 3 songs on there playlist, alambasterdam, falcor, and dandruff.

Russo

---

### Post by thorgal on 2008-07-26
Hi Russo,

who talks about rules ? what most ppl mention here are just ways to improve something. There's no golden recipe to get the best out of your audio chain but there are a few tricks or points in this chain one should pay attention to. At the end of the day, this is very subjective and depends a lot on the original vision the composer  had. The closer to that vision, the better, and if there is one "rule" I try to respect, it is this one principle. The rest is just technical tricks that may or may not work for you.

---

### Post by russo.mic on 2008-07-26
I'm not saying Why the rules here, I think you misunderstand me.

I grow weary of all the manuals and books about recording that state things like "1k is always the best place to eq an trumpet" and things like that. 

I was only stating that the first rule of recording is that there is no rules! 

Russo

---

