---
title: "Science Needs Your Brain"
date: 2009-03-22
forum: The Cafe
---

### Post by FaceLeg on 2009-03-22
I’ve spent the last 4 months helping Sam and Cathy (researchers at Waikato University) to develop and improve an algorithm that finds equivalent Wikipedia articles for existing Cyc concepts, and also discovers new concepts and adds them to the knowledge base. Discovery of new concepts is achieved by using a combination of Cyc’s inference engine, automated semantic disambiguation methods developed at the University of Waikato Digital Libraries Lab, Wikipedia’s category structure and infobox information, and parsing the first sentences of Wikipedia articles.

We need volunteers to help us evaluate our data. The evaluation will take about 25 minutes of your time, is straightforward, and quite interesting!

The aim of the evaluation is to determine whether our algorithm is smart as you are: whether it is as good as you are at saying which two concepts are related, and in what way.

Completing an evaluation will not only help us tremendously, it’ll also put you in the draw to win a US$25 Amazon.com voucher!

Were we successful in molding an algorithm with the same consistency in it’s conclusions as a group of humans?

Help us find out!

[Cyc evaluation]("http://wdm.cs.waikato.ac.nz/cyc/evaluation/")

More information about [Cyc]("http://en.wikipedia.org/wiki/Cyc") or [the Research ]("http://www.cs.waikato.ac.nz/~olena/cyc.html")

P.S. I created the evaluation using Eclipse & Aptana under Ubuntu ;), and the algorithm + evaluation code will both be released as open source when we've got our results

---

### Post by artilec on 2009-03-22
Hi faceleg, I have participated in the cyc evaluation and thought i'd share my thoughts.

Firstly, to be able to compare, your algorithm, with a human, you would need an equal set of rules.  An equal base to determine it's integrity.

Your algorithm has an advantage by definition. It has more rules, to base it's decision making. It knows how to determine it's decision, what Sub-level to gather its data and thus parse the result. 

Compare that, to the Human, a rules base of 'examples' and only a limited number at that.  We have nothing to work with to compete.

If a question has three possible ansews but has 5 or more associations only the algorithm will know best because of the human that matured it. It matures as the process evolves. It's a no win situation for the human to better.

There's no rules at the human level, We have nothing to work with. It's A rules base that matures by definition.  Hence we are the designers and so long as we understand the algorithm it will never be better than us.

A programmer could not write a complex program with a just a few snipets of code to work with.

quote from your post:

The aim of the evaluation is to determine whether our algorithm is smart as you are: whether it is as good as you are at saying which two concepts are related, and in what way.

Hmm. I notice you miss out the word 'as' before 'smart' in the first line. 

Interesting as this project is, you may want to consider releasing your source code as a better way of improving your AI.  Linux VS Windows springs to mind?

Good Luck!

Artilec

---

### Post by FaceLeg on 2009-03-23
> **artilec said:**
> Hi faceleg, I have participated in the cyc evaluation and thought i'd share my thoughts.

Thanks, we _really_ appreciate your help!

> **artilec said:**
> Firstly, to be able to compare, your algorithm, with a human, you would need an equal set of rules.  An equal base to determine it's integrity.

Your algorithm has an advantage by definition. It has more rules, to base it's decision making. It knows how to determine it's decision, what Sub-level to gather its data and thus parse the result.

I think I understand what you're saying here, but I disagree.  A Human has almost infinitely more rules to bring to bear on a decision.  Rules that have been learned over a lifetime.  An algorithm has only those rules that have been programmed into it and whatever data it is designed to read.  

The main point of the Cyc AI is to develop software that "has common sense" - something that knows that if you and I are eating lunch together, then you and I are not dead!  Cyc's goal is extremely difficult.

> **artilec said:**
> Compare that, to the Human, a rules base of 'examples' and only a limited number at that.  We have nothing to work with to compete.

In the future this could be so, but right now Humans are still beating software hands-down when it comes to making "human-like" decisions! Don't forget that we humans can learn and adapt - what you and I learn from reading a given Wikipedia Article will almost always teach us all we need to know to categorise the subject of the article into a Cyc collection, or to say (with extremely good accruacy) whether said article is equivalent to a given Cyc term.

While completing the algorithm you would have noticed that some of the mappings and/or new children were incorrect!  You (a human) used the same data that Cyc has - the description of the cyc term and the wikipedia page.  Our algorithm used clever techniques and Cyc's common-sense knowledge to determine its answer, and you used your common sense, reading ability and general knowledge.

We just want to know how the algorithm would compare to the agreement between evaluators - this is why we need _a lot_ of evaluators!

> **artilec said:**
> If a question has three possible ansews but has 5 or more associations only the algorithm will know best because of the human that matured it. It matures as the process evolves. It's a no win situation for the human to better. 

I'm sorry but I don't understand what you're saying here.

> **artilec said:**
> There's no rules at the human level, We have nothing to work with. It's A rules base that matures by definition.  Hence we are the designers and so long as we understand the algorithm it will never be better than us.

I thought you said (above) that we humans can't compete with an algorithm??

> **artilec said:**
> A programmer could not write a complex program with a just a few snipets of code to work with.

quote from your post:

The aim of the evaluation is to determine whether our algorithm is smart as you are: whether it is as good as you are at saying which two concepts are related, and in what way.

Hmm. I notice you miss out the word 'as' before 'smart' in the first line.

Thanks, I agree that a little more time spent proof-reading would have been a good thing.  

> **artilec said:**
> Interesting as this project is, you may want to consider releasing your source code as a better way of improving your AI.  Linux VS Windows springs to mind?

Perhaps you missed it:

> **FaceLeg said:**
> P.S. I created the evaluation using Eclipse & Aptana under Ubuntu ;), and the algorithm + evaluation code will both be released as open source when we've got our results

I wouldn't dare post about any non-open sourced research here!

> **artilec said:**
> Good Luck!

Artilec

Thanks :)

---

### Post by artilec on 2009-03-23
Artilec:-  If a question has three possible ansews but has 5 or more associations only the algorithm will know best because of the human that matured it. It matures as the process evolves. It's a no win situation for the human to better.

FaceLeg:- I'm sorry but I don't understand what you're saying here.

Artilec:- I,m struggling with lack of rules, your AI isn't ever going to have common sense so i,m looking for some common ground by which to compete, a rules base to compete with the AI.

a few examples of the sorts of questions in the evaluation:

is a door handle a lever? or a kind of lever? or not a lever?

is a colander a drainer or a kind or drainer

is a sock a barrier or a kind of barrier

is a cloth equivalent to a towel

is Final Fantasy equivalent to FinalFantasy

is a buckle a fastener or a kind of fastner

is a brook a stream or a kind of stream

is a bulb equivalent to a seed

The AI (algois a door handle a lever or kind of lever

is a collinder a drainer or a kind or drainer

is a sock a barrier or a kind of barrier

is a cloth equivelant to a towel

is Final Fantasy equivelant to FinalFantasy

is a buckle a fastner or a kind of fastner

is a brook a stream or a kind of stream

is a bulb equivelant to a seed 

I can answer these question to the best of my judgment, thus add to the collective judgments (with the assumption being that the same question is asked to a number of other humans) but i,m struggling to understand how the AI develops it,s common sense.  I,m assuming the algorithm is near complete and is at the point of self learning, but don't see how it can go on and answer these types of questions itself.  

Is it really AI?

Artilec:- Hmm. I notice you miss out the word 'as' before 'smart' in the first line.

FaceLeg:- Thanks, I agree that a little more time spent proof-reading would have been a good thing.

Artilec:- Only jokin, your keen to beat the Human as I am to beat the AI.

It's definitely a worthwhile project that I am happy to have contributed too, and again Best of Luck!!

Artilec

---

