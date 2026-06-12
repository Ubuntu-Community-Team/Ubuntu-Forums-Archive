---
title: "francophones: a new project"
date: 2007-04-26
forum: The Cafe
---

### Post by dbbolton on 2007-04-26
[http://sourceforge.net/projects/dictionnaire/](http://sourceforge.net/projects/dictionnaire/)

PM or email me if you're interested.

---

### Post by dbbolton on 2007-04-27
where's frodon when you need him.

---

### Post by maniacmusician on 2007-04-27
sounds interesting. What kind of help do you need?

---

### Post by starcraft.man on 2007-04-27
Ah ha... I was looking for a French dictionary. I assume this is the dictionary program that runs on your desktop. Is there a project going thats just a straight French only dictionary with definitions rather than translation? I really need one of those, would be awesome :)

---

### Post by dbbolton on 2007-04-27
> **maniacmusician said:**
> sounds interesting. What kind of help do you need?
well, to be frank: a lot.

i think what demands the most help is programming the interface to work with the database- as this is something where i have virtually no experience.

one person on sourceforge has offered to help specifically interface design.

i have a pretty good idea of how to set up an xml catalogue, but i am beginning to see that this alone will not suffice. for instance, if you look at an entry in a real dictionary, the text is formatted in various ways to indicate different things, which makes entries easier to read. one (admittedly rudimentary) solution is to employ xhtml and put the entire database online, then a front-end (much like the Dictionary app that is shipped with ubuntu) could be used to access the database.

however, i would ultimately like to create an internet-independent, mobile version of dictionnaire.

here is an example of the database
```
<?xml version="1.0" ?>
<dictionairre>
<prod id="a">
 <entry>
  <word>a</word>
  <phon>[&#601;]</phon>
  <partspeech>indef art</partspeech>
  <trans>un(e)</trans>
  <note>After a negative verb, "de" is used as the indefinite article</note>
  <ex lang="en">I have a car, but he doesn't have a car.</ex>
  <ex lang="fr">J'ai une voiture, mais il n'a pas de voiture.</ex>
 </entry>
 <entry>
  <word>abaci</word>
  <phon>[&#712;æb&#601;sa&#618;]</phon>
  <partspeech>n</partspeech>
  <def>pl. of abacus</def>
 </entry>
 <entry>
  <word>aback</word>
  <subhead>taken ~ (by)</subhead>
  <phon>[&#712;&#601;bæk]</phon>
  <partspeech>adv</partspeech>
  <trans>déconcerté(e) (par)</trans>
 </entry>
</prod>
</dictionnaire>
```
as you can see, it gets a bit sloppy.

so, i need brainstormers right now more than anything, really. i would also like to have native french speakers to help write usage notes in conjunction with native english speakers. another thing that is needed is sheer numbers. there's no way i will be able to type an entire dictionary alone.

---

### Post by dbbolton on 2007-04-27
> **starcraft.man said:**
> Ah ha... I was looking for a French dictionary. I assume this is the dictionary program that runs on your desktop. Is there a project going thats just a straight French only dictionary with definitions rather than translation? I really need one of those, would be awesome :)

that would be an excellent project. i've never heard of one though. if you find one that includes etymology, let me know. when i use a regular english dictionary (my native language) i find the etymology more helpful than the definitions, and this is something that i think would be helpful in learning foreign words.

for instance, a french word may look or sound completely different from its english equivalent, but the latin root of that french word might have given rise to an english cognate, making the new french word easier to "understand" rather than just "memorise."

---

### Post by dbbolton on 2007-04-29
i've set up a small wiki. everyone here is more than welcome to partake in the discussions or simply make suggestions:

[http://dictionnaire.wikispaces.com](http://dictionnaire.wikispaces.com)

---

