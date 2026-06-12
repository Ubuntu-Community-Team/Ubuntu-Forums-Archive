---
title: "My ideas and features of a good Koch method morse training program"
date: 2019-01-19
forum: Ubuntu, Linux and OS Chat
---

### Post by isprins on 2019-01-19
What is morse?
Morse code is a character encoding scheme used in telecommunication that encodes text characters as standardized sequences of two different signal durations called dots and dashes or dits and dahs. Morse code is named for Samuel F. B. Morse, an inventor of the telegraph.

The International Morse Code encodes the ISO basic Latin alphabet, some extra Latin letters, the Arabic numerals and a small set of punctuation and procedural signals (prosigns). Each Morse code symbol is formed by a sequence of dots and dashes. The dot duration is the basic unit of time measurement in Morse code transmission. The duration of a dash is three times the duration of a dot. Each dot or dash within a character is followed by period of signal absence, called a space, equal to the dot duration. The letters of a word are separated by a space of duration equal to three dots, and the words are separated by a space equal to seven dots. To increase the efficiency of encoding, Morse code was designed so that the length of each symbol is approximately inverse to the frequency of occurrence in text of the English language character that it represents. Thus the most common letter in English, the letter "E", has the shortest code: a single dot. Because the Morse code elements are specified by proportion rather than specific time durations, the code is usually transmitted at the highest rate that the receiver is capable of decoding. The Morse code transmission rate (speed) is specified in groups per minute, commonly referred to as words per minute.

Morse code is usually transmitted by on-off keying of an information carrying medium such as electric current, radio waves, visible light or sound waves.

How is the speed calculated ?
The word PARIS is the standard for determing CW code speed. Each dit is one element, each dah is three elements, intra-character spacing is one element, inter-character spacing is three elements and inter-word spacing is seven elements. The word PARIS is exactly 50 elements.
Note that after each dit/dah of the letter P -- one element spacing is used except the last one. (Intra-Character).
After the last dit of P is sent, 3 elements are added (Inter-Character). After the word PARIS - 7 elements are used.
Thus:
P = di da da di = 1 1 3 1 3 1 1 (3) = 14 elements
A = di da = 1 1 3 (3) = 8 elements
R = di da di = 1 1 3 1 1 (3) = 10 elements
I = di di = 1 1 1 (3) = 6 elements
S = di di di = 1 1 1 1 1 [7] = 12 elements
Total = 50 elements
() = intercharacter
[] = interword

If you send PARIS 5 times in a minute (5WPM) you have sent 250 elements (using correct spacing). 250 elements into 60 seconds per minute = 240 milliseconds per element.

13 words-per-minute is one element every 92.31 milliseconds.

What is the Koch method ?
Koch's method was invented by German psychologist Ludwig Koch in the 1930s.
It's a method of learning morse code.
Some explanation:
When you hear a morse code character, you should know, without thinking, what it is. It should be a reflex. In fact, copying above about 10 wpm can only be done by reflex.

That's why slow code is a deadly trap, and why traditional amateur methods of code training are so painful and frustrating. Most hams are told to memorize all the characters, then start building their speed. When you do it this way, you build a "lookup table" in your brain, comparing each character you hear with those in the lookup table until you find a match. This process shuts down from overload at about 10 wpm. That's why people experience a "plateau" at 10 wpm, and don't see any progress for weeks or months.

Those who finally get over that "hump" and progress beyond 10 wpm do so because, through constant practice, they have begun to copy code by reflex instead of by thought. They are the lucky ones; this 10 wpm barrier is where many folks give up out of frustration.

Code training, then, should completely bypass the lookup-table phase and begin by building copying proficiency as a reflex. This was recognized in the 1930s by the German psychologist Ludwig Koch, who devised the most efficient method known for Morse training.
Koch's method is a simple, direct way of building reflexes. Here's how it works:

You start out by setting up your computer (or a microprocessor-based code tutor machine) to send you Morse characters at 20 wpm and at an overall sending speed of at minimum 15 wpm. You then have the machine start sending -- but only two characters. That's right, for your first sessions, you'll only have two choices.

If your score is 90 percent or better -- congratulations! You just learned your first two characters, and, importantly, you learned them at full speed. You'll never have to learn them over again. If you didn't make 90 percent, practice some more. As soon as you can copy the first two characters with 90 percent accuracy, add a third character to your practice. Your accuracy will drop as you work on assimilating the new character, but it will rise again to 90 percent or better. Then you add the fourth character, and so on.
Most existing software does not progress automatically, at lest those I am aware of.

This method does not allow you to build that lookup table in your brain. To copy at full speed, you must build the reflexes in order to achieve 90 percent accuracy. And that's what you're spending your time doing -- building reflexes. Think of it as a parallel to perfecting a tennis swing or mastering a gymnastic routine; you're practicing until you get it right. The Koch method of building code proficiency character-by-character is similar to standard methods of teaching touch typing, another skill that must be reflexive.


How much time is required? That will depend on the individual. Koch himself, with hand-picked students, got a group to master 12 wpm code in a mere 13.5 hours!
You probably won't match that, but that's much faster than any other method in the psychological literature. You can get an idea of how long it's going to take after you've mastered a few characters. Keep track of your training sessions (some software will do this for you) and calculate your hours-per-character rate (or characters-per-hour if you're really fast!). That, multiplied by the 43 characters in the amateur Morse test, will give a rough idea of how long it's going to take.
This is a very individual method of training -- you progress at your own best speed, and spend only the time required to gain each new character. This means that you will waste no time in reaching your goal.

While the Koch method is the fastest method of Morse training, speed alone is not its principal advantage. Its principal advantage, and a major difference from other methods, is that it provides you with constant positive reinforcement. This begins with your realization, after mastering the first two characters, that you can copy code at 15 or 20 wpm, because you just did it. After that, each new character mastered is further proof of your progress. Contrast that to slowly trying to build speed up from 4 or 5 wpm, then hitting the plateau at 10 wpm and seeing no progress for a long time. With the Koch method, frustration is at a minimum.

Constant testing is necessary to ensure that you maximize the effectiveness of the Koch method.  Remember, if you score 90 percent accuracy or better, add another character. If you score any less than that, try again. By constantly testing yourself on continuous copying of at least five minutes, you know exactly how you're doing and exactly when you should add another character. This results in the fastest progress possible.

Naturally, with the Koch method, you'll be copying random groups of characters, rather than words, until you've mastered the entire character set.  This will ease the transition from random groups to actual words. Yes, there is a difference in the rhythm and "feel" of words and random groups. Once you've become accustomed to copying words, you should start copying sample QSOs, which are the format of the amateur tests. Pay special attention to callsigns, locations, and numerals; these are the types of things that can form questions on the test.

As you proceed toward your goal, remember that some days are just going to be better than others and some characters will take longer to assimilate than others. You know, however, that you can reach your goal because you've already mastered some characters and proven that copying at full speed is something you can do. Keep in mind that what you're doing is building reflexes, and that takes time. The amount of time you require has nothing to do with your intelligence; it's just how long it takes for characters to "sink in" and become part of your reflexes.

Compatibility: Linux Ubuntu and variants.

Inputs:
CW decoder using a soundcards mic input or products like Winkeyer.
That should enable use of a CW tone generator connected to a straight
key,iambic,paddles or bug. Standard inputs like a keyboard and mouse.

Training mode:
First the program sends a series of K's in CW for 30 seconds while the
character K is displayed. Then it repeats the procedure with the
character M.
When that is complete it sends a four characters  group using K and M in
random places without displaying the letters. It then waits for a four
characters input using the keyboard, shows the characters you have
gotten correct in green, the wrong ones in red. That continues until the
user has gotten 90 % correct of a number of groups, then a new letter is
introduced ( for example X ), it is sent for 30 seconds while the
character is displayed. 
Then the lesson continues using the new character until 90% of groups is
correct, a new character or prosign is introduced and the lessons
continues until all characters are learned. 

Sending mode:
A four character group using K and M at random places is displayed,the
program waits until  four characters have been decoded and shows the
characters you have gotten correct in green, wrong ones in red.
That continues until the user has gotten 90 % correct of a number of
groups, then a new letter is introduced and included in the group at random.

There should be not to harsh timing requirements on sending, some normal
slack should be permitted as long as the CW decoder can decode perhaps
60%~70% of the transmitted CW it should be good.

Notes:
The program should keep track of the characters and prosigns learned,
and perhaps prioritize the most common ones first, and when sufficient
numbers of characters and prosigns is known these are used to build
phrases and typical QSOs. It could also be connected to a score board,
so users can compare scores.
It should also support multiple users on the same software instance.
It should also display statistics of a users progress and time used.
The slowest permitted speed should be 15 WPM. It should also be possible
to adjust the mininum and maximum number of characters in the groups and
if they are of random size. Words should also be possible.

What is a QSO ?
An amateur radio contact, more commonly referred to as simply a "contact", is an exchange of information between two amateur radio stations. The exchange usually consists of an initial call, a response by another amateur radio operator at an amateur radio station, and possibly a signal report. A contact is often referred to by the Q code QSO. It is often limited to just a minimal exchange of such station callsigns. Stations who have made a contact are said to have worked each other. An operator may also say that he has worked a certain country. Amateurs use the slang expression ragchew or ragchewing to refer to an extended, informal conversation, a variation of the common idioms "chewing the fat" and "chewing the rag"
A QSO is a "Q" code, those are a standardized collection of three-letter codes all of which start with the letter "Q". It is an operating signal initially developed for commercial radiotelegraph communication and later adopted by other radio services, especially amateur radio. To distinguish the use of "Q" codes transmitted as questions from those transmitted as statements, operators used the Morse question "INT" (dit dit dah dit dah) as a prefix to the "Q" code.
Some examples of QSO's with CW:
[http://www.naqcc.info/cw_qsos.html](http://www.naqcc.info/cw_qsos.html)
[https://www.qsl.net/w8rit/how_to_make_a_cw_contact.htm](https://www.qsl.net/w8rit/how_to_make_a_cw_contact.htm)

Although Q codes were created when radio used Morse code exclusively, they continued to be employed after the introduction of voice transmissions. To avoid confusion, transmitter call signs are restricted; no country is ever issued an ITU prefix starting with "Q".
A list of "Q" codes commonly used by ham radio amateurs can be found here:
[https://www.amateur-radio-wiki.net/index.php?title=Codes_and_Alphabets#Q-Code](https://www.amateur-radio-wiki.net/index.php?title=Codes_and_Alphabets#Q-Code) 

A good list over prosigns used:
[https://en.wikipedia.org/wiki/Prosigns_for_Morse_code](https://en.wikipedia.org/wiki/Prosigns_for_Morse_code)

I know that it is possible to add QRM,signal fading ( the signal fades in and out of atmospheric noise ),pileups ( many stations calling you at the same time) stations working close to you, and noise to
imitate more "realistic conditions", as done with Kochmorse.
[https://github.com/hmatuschek/kochmorse](https://github.com/hmatuschek/kochmorse)
Perhaps even drifting and unstable tones is possible.

A example of how a pileup can sound like is:
[https://www.youtube.com/watch?v=SdHtqLPkXFo](https://www.youtube.com/watch?v=SdHtqLPkXFo)
The operator in the link above has skills as these can get really messy, a example is this mayhem:
[https://www.youtube.com/watch?v=LKlrTOhYk1Y](https://www.youtube.com/watch?v=LKlrTOhYk1Y)

Morse alphabets that should be used : Primarly International, but the
possibility to add regional extras like the Norwegian Æ Ø and Å. Those
extras should be possible to add to the characters learned with a option
in settings.
Also, support for wordlists in English or optional local languages.

A  QSO partner using Recurrent Neural Network (RNN ?
[http://ag1le.blogspot.com/2015/11/your-next-qso-partner-artificial.html](http://ag1le.blogspot.com/2015/11/your-next-qso-partner-artificial.html)

---

### Post by QIII on 2019-01-19
And?  What is it you want?

Not a support request.  Assuming that you are trying to generate discussion about doing something like this for the Linux community in general, moved to Ubuntu, Linux and OS Chat

---

