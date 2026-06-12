---
title: "Oh No!! Multicores turning computing on its head! Software techies *FLUMMOXED*!!"
date: 2008-08-14
forum: The Cafe
---

### Post by Sporkman on 2008-08-14
Don't worry - Microsoft's hard at work at saving us from this new, enormous challenge!

[http://money.cnn.com/2008/08/13/technology/microchips_copeland.fortune/index.htm?source=yahoo_quote](http://money.cnn.com/2008/08/13/technology/microchips_copeland.fortune/index.htm?source=yahoo_quote)

> **A chip too far?**

The latest microchips have gotten so complicated that companies from Microsoft to Apple to Intel say software writers can't keep up. The result could hurt computer sales.

By Michael Copeland, senior writer
August 14, 2008: 5:47 AM EDT

(Fortune Magazine) -- Could faster chips translate into slower computers? That's the sales-threatening prospect furrowing brows in every corner of the PC business, from industry titans such as Intel, Microsoft, and Apple (AAPL, Fortune 500) to major centers of academe.

For decades the PC industry has juiced performance - and sales - with a regular two-step dance. First, chipmakers jacked up the speed of their latest offerings. Then the software brains figured out how to turn all that processing power into faster operations and cool new functions.

But the latest generation of chips, known as multicore, are so complex and so qualitatively different from their predecessors that they have flummoxed software developers. "We've gone through changes in the past," says Craig Mundie, Microsoft's chief research and strategy officer. But this one, he says, is the most "conceptually different" change "in the history of modern computing."

The change was set in motion four years ago when Intel (INTC, Fortune 500) and others reached a point where they could no longer make single processors go faster. So they began placing multiple processors (or "cores") on a single chip instead.

That design, however, dramatically raises the level of difficulty for software developers. If they want to get the full oomph out of multicore chips, their applications need to break tasks apart into chunks for each core to work on, a process known as parallel computing. (Programs running on supercomputers have employed this technique for years to simulate atomic explosions or model complex aerodynamics.)

But programming in parallel is simply too complex for the average code writer, who has been trained in a very linear fashion. In conceptual terms, traditional coding could be compared to a woman being pregnant for nine months and producing a baby. Parallel programming might take nine women, have each of them be pregnant for a month, and somehow produce a baby.

That's a dramatic change, and battalions of techies from Redmond, Wash., to San Jose are struggling to figure it out. "If I were the computer industry, I would be panicked, because it's not obvious what the solution is going to look like and whether we will get there in time for these new machines," says Kunle Olukotun, a computer science professor who is attacking the multicore challenge at Stanford's new Pervasive Parallelism Lab. "It's a crisis, and I wonder whether what we are doing and what is happening within the industry is too little, too late."
Sales risk or opportunity?

Even the creators of multicore chips admit they're causing trouble. "I accept that parallel computing is a big problem," says Sean Maloney, executive vice president for sales and marketing at Intel. He says the company is hiring "a lot" of software people to tackle the challenge.

The use of chips with four cores in the past year has meant that such a PC today is no faster for many key tasks than, say, a comparable computer purchased three years before. Worse, with chips of six or more cores on the way, your favorite applications could actually run more slowly. That raises the prospect that customers will hold off on buying the next generation of computers, thus hammering sales.

It isn't the first time that the adoption of this sort of technology has caused havoc. Beginning in 2000, the videogame industry faced a similar challenge when Sony (SNE)'s then-dominant PlayStation shifted to chips with multiple, different processors for the PS2. The result, according to Neal Robison, director of software vendor relations at AMD (AMD, Fortune 500), was "blood and corpses everywhere."

Video companies struggled to adapt and lost sales as they fell behind on their product cycles. Giant Electronic Arts (ERTS) had to delay the release of its cash cow "NBA Live 2001" during the peak of basketball season. One company, Oddworld Inhabitants, even discontinued its popular "Abe's Oddysee" because it couldn't make the game function on the new system.

Something similar may take place in the PC world. Intel's Maloney asserts the problem will be solved "because the economic benefits are huge." And, he notes, "whoever figures out how to take advantage of multicore first could wreak some serious economic damage on their competition."

Microsoft (MSFT, Fortune 500)'s Mundie argues that the solution will mark a watershed: A new generation of killer applications will emerge, and the industry will take its next big leap, with wildly improved performance. That would put the business back on a path of sustainable steady growth. But that's still a ways off. "We are in a flat spot right now," he says. "What we don't know is for how long."

---

### Post by Paqman on 2008-08-14
Now, i'm not a code monkey, but I doubt that the idea that some tasks can be done as multiple threads is going to come as some kind of shock to software developers.

---

### Post by bonzodog on 2008-08-14
Isnt it lucky that the linux kernel has done multi-threading for years eh?

---

### Post by Paqman on 2008-08-14
> **bonzodog said:**
> Isnt it lucky that the linux kernel has done multi-threading for years eh?

What OS hasn't?

---

### Post by Alasdair on 2008-08-14
It may be too complex for the average programmer writing in a imperative language like C, but there is a lot of research aimed at creating languages and techniques that allow programmers to write multithreaded code while still remaining sane. Look at Haskell and Erlang for examples of languages that reduce the difficulty of writing multithreaded applications. Parallel programming is not an insurmountable problem.

---

### Post by sydbat on 2008-08-14
But look at who was interviewed...

---

### Post by Daveski on 2008-08-14
> But programming in parallel is simply too complex for the average code writer, who has been trained in a very linear fashion. In conceptual terms, traditional coding could be compared to a woman being pregnant for nine months and producing a baby. Parallel programming might take nine women, have each of them be pregnant for a month, and somehow produce a baby.

Sure, if an 'average code writer' is just someone who has carved out a living knocking out average VB or VBA code. With a good tool-chain, and toolkits which utilise multi-threading (surely object-oriented, and event-driven environments THRIVE on multi-threading even if the coder hasn't given much thought to parallel optimisation) this should not be considered a problem.

---

### Post by the yawner on 2008-08-14
> In conceptual terms, traditional coding could be compared to a woman being pregnant for nine months and producing a baby. Parallel programming might take nine women, have each of them be pregnant for a month, and somehow produce a baby.

Best layman translation...

---

