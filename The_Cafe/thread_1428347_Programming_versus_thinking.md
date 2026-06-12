---
title: "Programming versus thinking"
date: 2010-03-12
forum: The Cafe
---

### Post by weichimaster on 2010-03-12
Do you think that it is possible to programme a computer to do useful research into number theory?

I would say no. My reasoning is below - sorry for the length of this thread.

 Suppose you have programmed the [Peano axioms]("http://en.wikipedia.org/wiki/Peano_axioms") into a computer. Consider the following problem, known as Goodstein's theorem and taken from Roger Penrose's book "The Large, the Small, and the Human Mind" :

Take a postive integer, for example 283. Express it in binary. So ```
403=2^8+2^4+2^3+2^1+2^0.
```Express the exponents in this sum in binary, as follows:
```
403=2^(2^3)+2^(2^2)+2^(2^1+2^0)+2^0.
```Repeat this process until all exponents are in binary form:
```
403=2^(2^(2+1))+2^(2^2)+2^(2^1+2^0)+2^0

```Now iteratively apply the following two steps:
**Step 1**
Increase the base by 1.
So our new number is:
```
3^(3^(3+1))+3^(3^3)+3^(3^1+1)+1

```[B]Step 2
[/B]Subtract 1 from the result.
Now go onto step 1, and repeat.

Does this process terminate for all starting numbers?

It turns out that the algorithm is in fact a [Godel statement]("http://en.wikipedia.org/wiki/G%C3%B6del%27s_incompleteness_theorems") for the Peano axioms. That is, if the Peano axioms are consistent, then there is no way of proving that this process will terminate. So our computer is unable to determine if the process will halt or not.

However, a human mathematician can bring out the machinery of transfinite induction, and use it to prove that the algorithm does in fact halt for every starting number.

The process of researching maths requires thinking, which goes beyond blindly following axioms. Computers currently can merely follow axioms. Therfore humans are better at maths than computers.

---

### Post by carbz413 on 2010-03-12
On some of the proofs, a computer could be used to calculate some of them (They have been good with a few proofs of prime numbers that I needed it for). However, the proofs that need to be proven, it will be harder, since some of those proofs require abstract thinking, and I don't think we've come far enough yet in technology where this could happen. 

Will it happen? I have no idea, it is certainly possible. But, not yet.

---

### Post by koleoptero on 2010-03-12
Unfortunately your closing statement is true.

---

### Post by Post Monkeh on 2010-03-12
> **weichimaster said:**
>   Therfore humans are better at maths than computers. true. just because something is faster doesn't always make it better.

---

### Post by weichimaster on 2010-03-12
Penrose actually has a suggestion for the technological advances needed to get computers on a par with humans. He argues that there is large scale quantum coherence in the brain, and this enables thinking. Therefore quantum computers are potentially the biggest technoligcal advance the can happen for computing. 

(He loses me slightly at this point, since I'm a pure mathematican and I don't know much phcysics or neuro-science.)  I highly recommend his books, though, if this type of thing interests you.

---

### Post by Hyporeal on 2010-03-12
How ironic that you deny computers the "machinery" of transfinite induction and relegate them to the domain of the highly intuitive Peano axioms! A computer is perfectly capable of using any decidable axiom schema you can think of. If anything, computers are more suited to rigorous proofs in higher math than humans are.

On the other hand, the task of doing useful research in number theory is far more than proof crunching. You may wish to invent completely new axioms or leverage human intuition in a creative proof. This is for the artificial intelligence folks to figure out. Nevertheless, there is absolutely no proof-theoretical division between computers and humans.

(There is no disproof of such a division either, since we don't know everything about how the human brain might possibly work. However, keep in mind that even the proposed quantum computers would not be any more powerful from a proof standpoint than conventional computers. It seems unlikely to me that there's a hypercomputer siting in our heads.)

---

### Post by weichimaster on 2010-03-12
> **Hyporeal said:**
> How ironic that you deny computers the "machinery" of transfinite induction and relegate them to the domain of the highly intuitive Peano axioms! A computer is perfectly capable of using any decidable axiom schema you can think of. If anything, computers are more suited to rigorous proofs in higher math than humans are.

On the other hand, the task of doing useful research in number theory is far more than proof crunching. You may wish to invent completely new axioms or leverage human intuition in a creative proof. This is for the artificial intelligence folks to figure out. Nevertheless, there is absolutely no proof-theoretical division between computers and humans.

(There is no disproof of such a division either, since we don't know everything about how the human brain might possibly work. However, keep in mind that even the proposed quantum computers would not be any more powerful from a proof standpoint than conventional computers. It seems unlikely to me that there's a hypercomputer siting in our heads.)

You make a good point about allowing the silicon to have transfinite induction as an axiom. However, suppose we add that axiom to the computer's starting list of axioms. Or, more generally, we give the computer any consistent set of starting axioms.

The now exist an infinite number of Godel statements for the new axiom scheme. These statements are undecidable from the computer's starting point. (Technical point: I assume that the starting axioms are consistent.)

However, in reality the Godel statements will either be true or false, and not undecidable. They are, after all, just statements about positive integers. Human ingenuity will prove some of these Godel statements by moving outside the narrow bounds of the computer's axiom scheme.

Well, you might argue that that's not a problem - we can just add whatever the fleshy mathematicians have proved as new axioms for the silicon mathematicians. But this runs into problems, since the new axiom set will have Godel statements which humans can prove. There is an infinite loop, where humans need to plug more and more starting assumptions into the silicon mathematicians. 

(Wiles' proof of Fermat's last theorem if of course a pretty extreme example of human cleverness in action.)

The initial axiom set given to the computer is not critical to the argument. Whatever axiom set is used has the same Godel induced headaches. The thing I like about the example given is that the Godel statement produced is pretty understandable.

---

### Post by undecim on 2010-03-12
You and your mind are all results of interactions of matter in your brain and body.

Eventually, we will have learned enough about these interactions to simulate humans on computers.

---

### Post by uljanow on 2010-03-12
That's the Halting Problem. A PC can't even compute *everything*.

---

### Post by schauerlich on 2010-03-12
> **undecim said:**
> You and your mind are all results of interactions of matter in your brain and body.

Eventually, we will have learned enough about these interactions to simulate humans on computers.

I was never one for physicalism and strong AI.

---

### Post by Chronon on 2010-03-13
> **weichimaster said:**
> 
However, in reality the Godel statements will either be true or false, and not undecidable. They are, after all, just statements about positive integers. Human ingenuity will prove some of these Godel statements by moving outside the narrow bounds of the computer's axiom scheme.

I agree that until computers exhibit some authentic sort of AI, they will not be able to make the metamathematical step of posing a new set of axioms.  However, computers have certainly already proven themselves as useful tools in mathematics.  

I do share some apprehension about them taking over mathematics, however.  What do we do when the proofs generated by computers cannot be checked by a human any longer?  Does mathematics become a matter of faith?

---

### Post by ssam on 2010-03-13
any argument that 'proves' that a collection of silicon logic gates can't do a certain task applies equally to a collection of whatever atoms the brain is made of.

---

### Post by weichimaster on 2010-03-13
> **ssam said:**
> any argument that 'proves' that a collection of silicon logic gates can't do a certain task applies equally to a collection of whatever atoms the brain is made of.
I'm not sure that I agree with this. Whatever a computer does is generated by the algorithm it is following. However, researching maths is not about following an algorithm. Whatever algorithm is stipulated, there will be statements which cannot be decided by the algorithm, and humans will be able to prove some of these statements.

We broadly understand what happens to the particles in a computer. The computer uses a large number of transistors and what-not to manipulate and store what is interpreted as a sequence of 1s and 0s.

However, neuro science isn't as advanced and not no-one has a clue what the particles in my brain are doing when I decide to make a post, or make a coffee etc.

Also, physics doesn't understand fully how particles interact - I believe that there is no generally accepted theory unifying quantum mechanics and gravity.

So it's entirely possible that there is an interaction between (as yet) unknown physics and what happens in our brain. This phenomenon may be present in computers, but it is not exploited in computer design   

This gives an explanation of the non-algorithmic nature of mathematics, and a programme of research to generate a new type of computer which could begin to emulate humankinds' general aweseomeness.

---

### Post by Kdar on 2010-03-13
Computers can just add, they just do it very fast.

---

### Post by Hyporeal on 2010-03-13
> **weichimaster said:**
> You make a good point about allowing the silicon to have transfinite induction as an axiom. However, suppose we add that axiom to the computer's starting list of axioms. Or, more generally, we give the computer any consistent set of starting axioms.

The now exist an infinite number of Godel statements for the new axiom scheme. These statements are undecidable from the computer's starting point. (Technical point: I assume that the starting axioms are consistent.)

However, in reality the Godel statements will either be true or false, and not undecidable. They are, after all, just statements about positive integers. Human ingenuity will prove some of these Godel statements by moving outside the narrow bounds of the computer's axiom scheme.

Well, you might argue that that's not a problem - we can just add whatever the fleshy mathematicians have proved as new axioms for the silicon mathematicians. But this runs into problems, since the new axiom set will have Godel statements which humans can prove. There is an infinite loop, where humans need to plug more and more starting assumptions into the silicon mathematicians. 

(Wiles' proof of Fermat's last theorem if of course a pretty extreme example of human cleverness in action.)

The initial axiom set given to the computer is not critical to the argument. Whatever axiom set is used has the same Godel induced headaches. The thing I like about the example given is that the Godel statement produced is pretty understandable.

The problem with the example is that Peano arithmetic does not uniquely define the natural numbers. It applies to an infinitude of nonstandard models as well, some of which actually refute the example theorem. Therefore, one can interpret the problem as being ill-defined. To give the computer a fighting chance, you need to give it enough axioms to completely define the problem. (This probably means using higher-order logic.)

Beyond the example, you make a seductive argument regarding the inevitable existence of unprovable true statements. I have two objections. First, who is to say that we humans are choosing correct axioms? Is the Axiom of Choice correct? Are the intuitionists correct in rejecting the law of the excluded middle? At some point it comes down to mathematical philosophy, where there are no rigorously right or wrong answers. As soon as you define a rigorous metamathematical framework for defending your axioms, you allow a computer to do the same.

The second objection is that the Godel statements for a particular formal system are not necessarily very interesting. I see this the same way I see the Halting Problem. A lot of programs will readily submit to a halt analysis, but a troublesome category of programs won't. (Some really fiendishly complex programs can be correctly analyzed by a simple technique. I think many people would be surprised at how solvable the Halting Problem really is.) Likewise, the Godel statements of a powerful arithmetic might not be interesting (or even comprehensible) to us at all. We already have a logic capable of proving Fermat's Last Theorem (which was widely but incorrectly speculated to be a Godel statement). Imagine the wealth of knowledge a computer could acquire from this system! I'm not convinced that an ad infinitum addition of new axioms is necessary to prove everything we'd be interested in knowing.

---

### Post by ssam on 2010-03-13
for anyone who is interested in the thread the book Godel Escher Bach, by Douglas Hofstader is a very good read.

---

### Post by Hyporeal on 2010-03-14
> **Chronon said:**
> I do share some apprehension about them taking over mathematics, however.  What do we do when the proofs generated by computers cannot be checked by a human any longer?  Does mathematics become a matter of faith?

Quite the opposite. Computer-assisted proofs generally meet a higher standard of rigor than their hand-written counterparts. Since proofs can be mechanically checked, you only need faith in the proof checker and not the proof generator. These checkers are small programs that can be tested extensively and manually analyzed for defects. Multiple checkers can be independently implemented and compared. By my reckoning, there's less faith required in that system than there is in the current peer review process for mathematics.

---

### Post by madjr on 2010-03-14
> **weichimaster said:**
> Do you think that it is possible to programme a computer to do useful research into number theory?

I would say no. My reasoning is below - sorry for the length of this thread.

 Suppose you have programmed the [Peano axioms]("http://en.wikipedia.org/wiki/Peano_axioms") into a computer. Consider the following problem, known as Goodstein's theorem and taken from Roger Penrose's book "The Large, the Small, and the Human Mind" :

Take a postive integer, for example 283. Express it in binary. So ```
403=2^8+2^4+2^3+2^1+2^0.
```Express the exponents in this sum in binary, as follows:
```
403=2^(2^3)+2^(2^2)+2^(2^1+2^0)+2^0.
```Repeat this process until all exponents are in binary form:
```
403=2^(2^(2+1))+2^(2^2)+2^(2^1+2^0)+2^0

```Now iteratively apply the following two steps:
**Step 1**
Increase the base by 1.
So our new number is:
```
3^(3^(3+1))+3^(3^3)+3^(3^1+1)+1

```[B]Step 2
[/B]Subtract 1 from the result.
Now go onto step 1, and repeat.

Does this process terminate for all starting numbers?

It turns out that the algorithm is in fact a [Godel statement]("http://en.wikipedia.org/wiki/G%C3%B6del%27s_incompleteness_theorems") for the Peano axioms. That is, if the Peano axioms are consistent, then there is no way of proving that this process will terminate. So our computer is unable to determine if the process will halt or not.

However, a human mathematician can bring out the machinery of transfinite induction, and use it to prove that the algorithm does in fact halt for every starting number.

The process of researching maths requires thinking, which goes beyond blindly following axioms. Computers currently can merely follow axioms. Therfore humans are better at maths than computers.


Dude you're crazy

u want a computer to do what You Can Do by giving it a few lines of code?

with those few lines you gave it, you (yourself) would not know the results to your math problem either.

we give putters processes and they process them, so if the process doesn't work its clearly your (human) fault 

people have invested over 20 years on you (and countless hundreds in researching), just so you can resolve that math problem

machines will never be perfect, they can never spontaneously (after certain conditions) appear in the universe like living cells. extinction is never the end of life. life could very well be immortal in the multiverse

AI software will eventually get better, its a matter of how many man-hours/resources we focus on it.

but we gotta take it slow, we dont want to create the next terminator

---

### Post by weichimaster on 2010-03-14
> **madjr said:**
> Dude you're crazy

This is possibly true. I find this very entertaining:
[http://www.youtube.com/watch?v=xp9Gm-aRe5A](http://www.youtube.com/watch?v=xp9Gm-aRe5A)

I'm also drunk, so I will reply to the more serious points in this thread tomorrow. In the meantime, chimpanzees and Segways are a great mixture, IMHO.

---

### Post by Chronon on 2010-03-14
> **Hyporeal said:**
> Quite the opposite. Computer-assisted proofs generally meet a higher standard of rigor than their hand-written counterparts. Since proofs can be mechanically checked, you only need faith in the proof checker and not the proof generator. These checkers are small programs that can be tested extensively and manually analyzed for defects. Multiple checkers can be independently implemented and compared. By my reckoning, there's less faith required in that system than there is in the current peer review process for mathematics.

You have argued well.

---

### Post by lisati on 2010-03-14
> **Kdar said:**
> Computers can just add, they just do it very fast.
I remember one of the teachers at my school 30-something years ago making a comment to the effect that it's amazing what a computer can achieve on the basis of "one and one is two". These days, with a little more experience under my belt, the pedantic side of my makeup would probably amend that to "one and one is one".
> **Hyporeal said:**
> Quite the opposite. Computer-assisted proofs generally meet a higher standard of rigor than their hand-written counterparts. Since proofs can be mechanically checked, you only need faith in the proof checker and not the proof generator. These checkers are small programs that can be tested extensively and manually analyzed for defects. Multiple checkers can be independently implemented and compared. By my reckoning, there's less faith required in that system than there is in the current peer review process for mathematics.

... as long as we can figure in a way of dealing with the [halting problem]("http://en.wikipedia.org/wiki/Halting_problem").This would probably mean that each checker would focus on a subset of possible tasks, and the results from all the checkers would subsequently collated.

---

### Post by Lux Perpetua on 2010-03-14
> **lisati said:**
> ... as long as we can figure in a way of dealing with the [halting problem]("http://en.wikipedia.org/wiki/Halting_problem").This would probably mean that each checker would focus on a subset of possible tasks, and the results from all the checkers would subsequently collated.What does the halting problem have to do with Hyporeal's remarks?

---

### Post by weichimaster on 2010-03-16
> **Hyporeal said:**
> Beyond the example, you make a seductive argument regarding the inevitable existence of unprovable true statements. I have two objections. First, who is to say that we humans are choosing correct axioms? Is the Axiom of Choice correct? Are the intuitionists correct in rejecting the law of the excluded middle? At some point it comes down to mathematical philosophy, where there are no rigorously right or wrong answers. As soon as you define a rigorous metamathematical framework for defending your axioms, you allow a computer to do the same.


I think you're right that this may well down philosophy as much as mathematics. My personal belief is that research maths is not algorithmic. Virtually no mathematicians in the course of doing their day job spend time wondering if they've used the axiom of choice or the generalised continuum hypothesis or another different axiom. 

My personal view is that there is an idealised mathematical world where the positive integers exist. (I'm a Platonist.) Defining the integers in the real universe is tricky, because  the universe is finite (although it's very, very big.) In my idealised world, every statement about integers is either true or false. Any axiomitic system is just an attempt to model the idealised world.


[QUOTE=]
The second objection is that the Godel statements for a particular formal system are not necessarily very interesting. I see this the same way I see the Halting Problem. A lot of programs will readily submit to a halt analysis, but a troublesome category of programs won't. (Some really fiendishly complex programs can be correctly analyzed by a simple technique. I think many people would be surprised at how solvable the Halting Problem really is.) Likewise, the Godel statements of a powerful arithmetic might not be interesting (or even comprehensible) to us at all. We already have a logic capable of proving Fermat's Last Theorem (which was widely but incorrectly speculated to be a Godel statement). Imagine the wealth of knowledge a computer could acquire from this system! I'm not convinced that an ad infinitum addition of new axioms is necessary to prove everything we'd be interested in knowing.[/QUOTE]I agree that a lot of the Godel statements will be very uninteresting. However, they will be true or false (although this is admittedly only due to my Platonic outlook.) And if humans can prove  Godel statements, they have a huge edge over computers in terms of the number of theorems they can prove.

> 
The problem with the example is that Peano arithmetic does not uniquely define the natural numbers. It applies to an infinitude of nonstandard models as well, some of which actually refute the example theorem. Therefore, one can interpret the problem as being ill-defined. To give the computer a fighting chance, you need to give it enough axioms to completely define the problem. (This probably means using higher-order logic.)
You are absolutely correct that the Peano axioms do not uniquely define the natural numbers. However, the same argument will in fact apply to whatever axiom scheme you choose. (This point may have a dependency on my Platonic world existing, though.)

Statements about natural numbers are either true or false. Any axiom scheme will have statements which it cannot prove. Therefore all axiom schemes will apply to non-standard models as well as my idealised Platonic natural numbers. So no axiom scheme can ever adequately define the natural numbers.  


Sorry for re-ordering your reply, but I thought my argument flowed better if I took things in this order.

---

### Post by lisati on 2010-03-16
> **Lux Perpetua said:**
> What does the halting problem have to do with Hyporeal's remarks?

What I'm thinking is that some proofs will need the benefit of human insight, because some tasks can't easily be solved algorithmically.

---

### Post by weichimaster on 2010-03-16
I wholeheartedly agree with the comments around how useful computers are currently as tools in mathematics. The first example I'm aware of is computers proving the [four colour theorem]("http://en.wikipedia.org/wiki/Four_color_theorem"). Humans worked on the problem, and managed to show that proving a large number (but finite) of cases was sufficient to prove the theorem. Checking the cases was largely mechanical, and so was done by a computer. 

There was bit of debate at the time as to whether the proof actually was vaild or not, since it was not done or checked by humans. However, it's now largely accepted.

I used computers pretty extensively when I researched things. There was a technical theorem (in singulairty theory) which made the classification of singularities an exercise in tedious algebra. This algebra was coded into a Maple programme, which made my life a lot easier.

But in both of these cases, the work requiring deep thinking was done by humans. In the four colour theorem, it was the initial split into a finite number of cases. With singularity theory, it was the proof of the intial theorem that turned the classification into algebra. My argument is that unless computers advance in a fundamental way, this type of split is likely to persist.   (@madjr, I will not advance an opinion on whether this advance is likely to create time travelling killer robots from the future.)

---

