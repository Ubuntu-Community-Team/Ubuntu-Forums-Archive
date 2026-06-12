---
title: "Obfuscated GPL'd code a violation?"
date: 2011-07-29
forum: The Cafe
---

### Post by occams_beard on 2011-07-29
Hi,

I am using a Javascript library that is dual licensed under GPL v3, and the author's own commercial license.  (They sell the library also under the commercial license for $500)

However, the code is obfuscated. E.g all white space has been removed, variable and function names have been changed to single characters and numbers. It is simply un-readable.

Would this not be a violation of the GPL?  I am certain they do not write the code like this, and it is obvious it's been run through an obfuscator. 

I've asked on their forum if they have the un-obfuscated code, but never got an answer.

I am hesitant to name any names, as the library is insanely useful, and I do not want to dissuade them from ditching the GPL license. But I want to see the code gosh darn it! :)

---

### Post by insane_alien on 2011-07-29
obfustication is annoying but its not illegal. it is still valid code.

---

### Post by johnl on 2011-07-29
> **occams_beard said:**
> Hi,

I am using a Javascript library that is dual licensed under GPL v3, and the author's own commercial license.  (They sell the library also under the commercial license for $500)

However, the code is obfuscated. E.g all white space has been removed, variable and function names have been changed to single characters and numbers. It is simply un-readable.

Would this not be a violation of the GPL?  I am certain they do not write the code like this, and it is obvious it's been run through an obfuscator. 

I've asked on their forum if they have the un-obfuscated code, but never got an answer.

I am hesitant to name any names, as the library is insanely useful, and I do not want to dissuade them from ditching the GPL license. But I want to see the code gosh darn it! :)

Javascript is often compressed in the way you described to reduce file size and download time for the user's browser.  It would be unusual not to provide a well-formatted version, though.

---

### Post by Thewhistlingwind on 2011-07-29
My memory is fuzzy since my last reading of the GPL and I am not a lawyer, but no?

However, it's certainly not in the spirit of the GPL.

You'd be hard pressed to sue the copyright holder for a violation of their own license, regardless.

---

### Post by occams_beard on 2011-07-29
They do not provide the un-miniified version...

---

### Post by zekopeko on 2011-07-29
> **occams_beard said:**
> Hi,

I am using a Javascript library that is dual licensed under GPL v3, and the author's own commercial license.  (They sell the library also under the commercial license for $500)

However, the code is obfuscated. E.g all white space has been removed, variable and function names have been changed to single characters and numbers. It is simply un-readable.

Would this not be a violation of the GPL?  I am certain they do not write the code like this, and it is obvious it's been run through an obfuscator. 

I've asked on their forum if they have the un-obfuscated code, but never got an answer.

I am hesitant to name any names, as the library is insanely useful, and I do not want to dissuade them from ditching the GPL license. But I want to see the code gosh darn it! :)

IIRC Javascript is usually optimized for sending by doing exactly what you described. A few KBs spread over millions of users adds up in bandwidth costs. Did you get the library by downloading if from their SVN/git repo or by taking it from some website that was using it? It could explain why it's unreadable.

Now if the author offers a commercial license that implies he owns the whole copyright on the code. As such he can release it in any way he so desires.

---

### Post by doas777 on 2011-07-29
yeah. technically that is not obfuscation, but optimization. i understand your frustration however. 

.js files are optimized this way because they have to be downloaded to the client in text, so every space or character in the var/method name adds an additional byte.

---

### Post by forrestcupp on 2011-07-29
While not probable, it is possible to write code that way. I don't think the GPL can dictate how someone writes their code.

Like it was already said, this is kind of contradictory to the heart of the GPL, but I really doubt if anything can be done about it.

---

### Post by occams_beard on 2011-07-29
> **Thewhistlingwind said:**
> My memory is fuzzy since my last reading of the GPL and I am not a lawyer, but no?

However, it's certainly not in the spirit of the GPL.

You'd be hard pressed to sue the copyright holder for a violation of their own license, regardless.

Well, I don't want to sue any one. I just want to see the code.

Would this not be the same as providing say for example compiled Java classes? Java byte code can be decompiled back into java source code (albiet unreadable source code)

---

### Post by occams_beard on 2011-07-29
> **zekopeko said:**
> IIRC Javascript is usually optimized for sending by doing exactly what you described. A few KBs spread over millions of users adds up in bandwidth costs. Did you get the library by downloading if from their SVN/git repo or by taking it from some website that was using it? It could explain why it's unreadable.

Now if the author offers a commercial license that implies he owns the whole copyright on the code. As such he can release it in any way he so desires.

Nope, right from their download page which says it is licensed under the GPL.  From what I can tell, they do not provide access to their VCS.

---

### Post by TheSqueak on 2011-07-29
From section 1 of the [GPLv3]("http://www.gnu.org/copyleft/gpl.html")


> 1. Source Code.

The “source code” for a work means the preferred form of the work for making modifications to it.

---

### Post by doas777 on 2011-07-29
> **occams_beard said:**
> (albiet unreadable source code)

thats the crux of it. disassembly always introduces this issue, because var/method's exist as addresses rather than string-based names. 

lots of people do it. it's as much art as science though. start by making a spreadsheet of the vars/methods, and I then would start working backward throught the methods and isolate the shared vars each uses, and then start trying to determine the purpose of each method. 
then just refactor them to use your names.

sounds easier than it is though, especially in a weak typed langague like javascript.

---

### Post by koenn on 2011-07-29
I think the FSF's view on this is that source code is what a programmer writes. The GPL being based in copyright, i.e. referring to text written by a human author, seems to support that.

In that view, an obfuscated/optimized/compacted javascript program is the output of source code processed by a compactor/obfuscater/... tool, and if the program is licensed under the GPL, you"d be entitled to the human-written sources of it.

---

### Post by Bachstelze on 2011-07-29
1. The author has every right to do whatever he wants with his code, so technically, the author *can not* violate the GPL as far as his code is concerned.

2. Whether or not code obfuscation violates the "preferred form" provision of the GPL has not been tested in court as far as I know, but it's not obvious IMO. I could see a good lawyer winning a case either way.

---

### Post by 3Miro on 2011-07-29
You should be able to run some program to fix the alignment at least. It may not fix the variable names, but those should be easier to fix after you have the proper indentation.

Some languages like Python and Fortran specify how you must indent, but no official specification states how C or JavaScript should be. This would be an interesting case for court.

---

### Post by Dave_L on 2011-07-29
> **TheSqueak said:**
> From section 1 of the [GPLv3]("http://www.gnu.org/copyleft/gpl.html")> 1. Source Code.

The “source code” for a work means the preferred form of the work for making modifications to it.

In my opinion, that clearly means that the obfuscated or optimized code is object code and not source code; therefore the "source code" should be separately available.

The fact that it's possible, although difficult, to understand and modify obfuscated or optimized code is not relevant. You could say the same thing about compiled object code.

---

### Post by ve4cib on 2011-07-29
I don't see how one could realistically argue that optimized/obfuscated code for an interpreted language is not the "preferred format for editing."  The file is still a plain-text .js file.  It's perfectly editable.  And because it's interpreted, it is still source code.  I just don't see an argument that would convince me that this -- admittedly annoying -- practice is in violation of the license.

---

### Post by ScionicSpectre on 2011-07-29
I don't see how something annoying could be preferable for editing. I could be twisting your words, though... hey, maybe I should be a lawyer! :D

---

### Post by occams_beard on 2011-07-29
> **ve4cib said:**
> I don't see how one could realistically argue that optimized/obfuscated code for an interpreted language is not the "preferred format for editing."  The file is still a plain-text .js file.  It's perfectly editable.  And because it's interpreted, it is still source code.  I just don't see an argument that would convince me that this -- admittedly annoying -- practice is in violation of the license.

I would say because it is not the "source" code.  It's been run through and optimizer/obfuscator.  Sure, you can still edit it, but you can also theoretically edit compiled code with a hex editor. Who is to say that is not the "preferred format?"

---

### Post by LemursDontExist on 2011-07-29
> **ve4cib said:**
> I don't see how one could realistically argue that optimized/obfuscated code for an interpreted language is not the "preferred format for editing."  The file is still a plain-text .js file.  It's perfectly editable.  And because it's interpreted, it is still source code.  I just don't see an argument that would convince me that this -- admittedly annoying -- practice is in violation of the license.

Well, if such a claim went to court, the putative violator would have to claim that he wrote most of the code in the optimized version directly rather than writing it and then running it through an optimizer - a pretty ridiculous claim.  The plaintiff could then bring in all sorts of expert witnesses who would testify that no one writes code that way, and that the code was clearly run through an optimizer.  Contrary to popular belief, a ridiculous but possibly true claim doesn't generally stand up in court.

That said, as others have pointed out, the copyright owner isn't subject to the GPL.

*That said*, I find it very unlikely that the source code has been released under the GPL and *isn't* available somehow in non-optimized form.  I suspect that the copyright owner just hasn't made any effort to make it easy to find since most javascript users aren't interested in reading/editing source code.

EDIT:
On reflection, I think a judge might well interpret "preferred form" to mean the form that the initial copyright holder used for distribution, in which case, if no other version is available any changes should also be distributed optimized to comply with the GPL in this case?  I could see it going either way.  In any case, the point about the copyright owner being able to do whatever he wants with the code stands.

---

### Post by occams_beard on 2011-07-29
> **LemursDontExist said:**
> 
*That said*, I find it very unlikely that the source code has been released under the GPL and *isn't* available somehow in non-optimized form.  I suspect that the copyright owner just hasn't made any effort to make it easy to find since most javascript users aren't interested in reading/editing source code.

jeasyui.com is it. If someone can find the un-minified source I'd be a happy camper :)

I've asked on their forum, but no-one ever replied. They might be busy or something, who knows.

---

### Post by ve4cib on 2011-07-29
> **occams_beard said:**
> I would say because it is not the "source" code.  It's been run through and optimizer/obfuscator.  Sure, you can still edit it, but you can also theoretically edit compiled code with a hex editor. Who is to say that is not the "preferred format?"

I think the key question is "what do they mean by 'preferred format?'"  That could, in my view, mean two things:

1- File format
2- Contents of the file

If we interpret "preferred format" to mean a digital format in which changes are easily made, then an obfuscated plain-text file fulfills the requirements.  The file is a format that is easy to edit.  Yes, the contents are cumbersome, but they are easy to edit.

If we interpret "preferred format" to mean the contents of the file, then obviously the obfuscated code would violate this.  But I just can't see any judge ruling that this is the correct interpretation, unless the GPL makes this point more explicitly.

---

### Post by occams_beard on 2011-07-29
> **ve4cib said:**
> I think the key question is "what do they mean by 'preferred format?'"  That could, in my view, mean two things:

1- File format
2- Contents of the file

If we interpret "preferred format" to mean a digital format in which changes are easily made, then an obfuscated plain-text file fulfills the requirements.  The file is a format that is easy to edit.  Yes, the contents are cumbersome, but they are easy to edit.

If we interpret "preferred format" to mean the contents of the file, then obviously the obfuscated code would violate this.  But I just can't see any judge ruling that this is the correct interpretation, unless the GPL makes this point more explicitly.


Actually the GPL says "preferred form for making modifications."  So I think it is obvious it is referring to the unobfuscated source code.

In any case, I think maybe "violation" in the title of this thread is the wrong word.  If I elect to use their code under the GPL, then would I not be entitled to the un-altered source code?

---

### Post by LemursDontExist on 2011-07-29
> **occams_beard said:**
> Actually the GPL says "preferred form for making modifications."  So I think it is obvious it is referring to the unobfuscated source code.

In any case, I think maybe "violation" in the title of this thread is the wrong word.  If I elect to use their code under the GPL, then would I not be entitled to the un-altered source code?

By releasing code under the GPL the author isn't giving up his own copyright or his right to release the code in any form he likes.

As far as I can tell, there's nowhere in the GPL where the author promises to provide the code in the "preferred form".  Certainly if someone else were distributing a modified copy of the code there'd be some question about how they're allowed to release it, but the original copyright owner is allowed to release his code in any form he wants.  

This may not be in the spirit of the GPL, and using the GPL makes very little sense if they intended not to release the human readable source, but I can't see a way in which the author could be held to have violated anything.

---

### Post by ScionicSpectre on 2011-07-30
Oh wow, he's right. D: Sad sauce.

---

### Post by koenn on 2011-07-30
You could simply ask yourself which files the _original author_ of the program would edit if he wanted or needed to make a modification to his program. Those files would be "source". 
In the case of compacted javascript, I'm guessing this would be the non-compacted files. 

In the GPL the author grants the right to modify the program to  third parties. Making source code available is a consequence of that.
I don't quite understand why the author of a program would say something like "you have the right to modify [the source code of] this program, but you can't have [a copy of] the source code".
There's something weird about that ....

---

### Post by ve4cib on 2011-07-30
There's also the possibility that the GPL is simply applied to the obfuscated code *after* it has been obfuscated, and is then released as a one-time, no-maintenance project.

Any time the author wants to make a change to what he's released, he goes back to his non-GPL, formatted source, changes things, runs that code through the obfuscator, and then releases the newly obfuscated code as a new product and slaps the GPL on it again.  He will never make changes to it, and therefore can argue quite soundly that this is "his preferred format for editing" since it's a freely editable piece of source code.  The fact that he has no intention of maintaining it at all is irrelevant.  He is providing what is, de facto, the source code, since by definition any piece of JS code *is* source code that is run through an interpreter.  And every subsequent GPL'd release is in essence a brand-new product, based on non-GPL'd code.

I'll admit it's a bit of a round-about way of doing it, but to my non-lawyer brain it seems reasonable.  I won't deny that it's a jerk move, but I don't see any legal issues with it.

---

### Post by forrestcupp on 2011-07-31
> **koenn said:**
> I think the FSF's view on this is that source code is what a programmer writes. The GPL being based in copyright, i.e. referring to text written by a human author, seems to support that.

In that view, an obfuscated/optimized/compacted javascript program is the output of source code processed by a compactor/obfuscater/... tool, and if the program is licensed under the GPL, you"d be entitled to the human-written sources of it.

But the obfuscated code is also code in written form. If they tacked the GPL license onto the code after it was obfuscated, that is the written code that is licensed. They could have put the GPL on the original code, but the GPL doesn't take effect until the code is distributed. So, since the obfuscated code in written form is what received the GPL, and that is what was distributed, I don't think there is anything that can be done about it.

Edit: I posted this before I read what ve4cib wrote right before my post. I usually don't make that mistake. :)

---

### Post by Sef on 2011-07-31
Since no one seems to be a lawyer, this thread is closed. If you feel that the GPL has been violated, click [here]("http://www.gnu.org/licenses/gpl-violation.html") to find out how to report the violation.


> 1. The author has every right to do whatever he wants with his code, so technically, the author can not violate the GPL as far as his code is concerned.

The author can do what they want with their code; however, if they put it under the GPL, then they have to follow the GPL.

---

