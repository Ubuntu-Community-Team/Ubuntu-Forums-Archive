---
title: "HTML computer language or not?"
date: 2011-07-03
forum: The Cafe
---

### Post by Linux_junkie on 2011-07-03
I was having a conversation the other day from a younger guy who was trying to convince me that HTML is a computer language and that made him a computer programmer.  I, on the other hand, disagreed with him.

I'm just interested to know if anyone else thinks or treats HTML as a computer language?   If you do think it is a computer language what makes you believe this?  Am I wrong in my thinking?

---

### Post by smellyman on 2011-07-03
it's a markup language, not programming.

HTML is very easy to learn.  start throwing in some Javascript or php then it is a different story.

---

### Post by Ctrl-Alt-F1 on 2011-07-03
HTML is not a programming language.  It is a language that describes the structure of a web page.  That is all.  It can't make any decisions.  Your friend is not a programmer.

However, if he uses JavaScript, PHP, C#, etc, then he is in fact programming.

---

### Post by ve4cib on 2011-07-03
HTML *is* a "computer language" in that it is a language used by computers.  It does a good(-ish) job of organizing static content in a document so that it can be displayed in a browser.  But that's all HTML does.

"Computer languages" would presumably include programming/scripting/assembly languages, machine code, markup languages, network protocols, and any other set of rules used by computers to transmit, receive, manipulate, and represent data.

However, a markup language, like HTML, is not a programming language.  Programming languages are used -- by programmers -- to write instructions that are executed by the computer.  HTML is not executed, and therefore is not a programming language.

As Ctrl-Alt-F1 points out though, there are many programming languages that are used in conjunction with HTML.  PHP, ASPX, Javascript, Java, Perl, Python, etc...  If he uses any of those to process, generate, or manipulate HTML then he is a a programmer.

But simply writing some HTML tags in a text editor does not make you a programmer anymore than sewing a button on a shirt makes you a tailor.

---

### Post by 1clue on 2011-07-03
ve4cib++

HTML/XHTML/XML/css are all markup in the context of web pages.  The are examined by a rendering engine to create a visual result.  The engine is not "executing" the markup.

That said, modern web pages almost all have some sort of dynamic component which cannot be described is pure HTML.  Any number of real languages are used in conjunction with HTML/XHTML/XML/css to get the desired result, and those are real languages.

There are dozens or hundreds of commonly used web frameworks that combine markup and executable code in often wonderful ways.  A web browser is a universal client and markup is a good shorthand on how to create the page reasonably faithfully.

---

### Post by Bandit on 2011-07-03
I agree with the above 4 post.

Its a markup language that can not be used to manipulate a data string or perform different process based on a set of variables.

Introduce him to PHP and Javascript. Those would be great languages for him to start to learn on his way to programming and can be very fun.

---

### Post by PartisanEntity on 2011-07-03
Even the name itself tells you what it is, it's markup, it is a language to *describe* content, not to develop processes.

I see it often even in job descriptions, many companies state they are looking for HTML "programmers", I am always tempted to contact them and tell them that HTML is not programming, HTML is describing ;-)

---

### Post by forrestcupp on 2011-07-03
> **ve4cib said:**
> HTML *is* a "computer language" in that it is a language used by computers.

...

However, a markup language, like HTML, is not a programming language.

Right.

Your friend was technically half correct if he said "computer language", but incorrect when he said he's a programmer. Markup languages just set appearances, but they don't have any code logic and conditions to them. He's only a programmer if he can write code logic that has conditions.

---

### Post by 3Miro on 2011-07-03
Being skilled in HTML makes you a web designer, which is a form of a computer artist. It is more computer oriented than regular artists, but it is an artist never the less.

C/C++, PHP, Java, Python, Perl and even JavaScript are programming languages and being skilled in those would make you a web-developer (i.e. a programmer for the Internet). With all of the above (maybe except PHP) you can make non-Internet programs, then you are just a developer (without the web).

Note that in all cases we are talking about some skill. Writing "Hello World" program doesn't make you a programmer.

The only "language" that I am unsure about is XML. I think it is borderline programming and it is hard to classify.

---

### Post by SeijiSensei on 2011-07-03
> **3Miro said:**
> With all of the above (maybe except PHP) you can make non-Internet programs, then you are just a developer (without the web).

You can write PHP scripts that don't involve the web at all.  You just run them from the command line with "php /path/to/myscript.php".  I've written a number of scripts in PHP to do administrative tasks.  One example is a script that runs nightly which scans all the users' inboxes and archives messages older than a certain date.  In this case I took advantage of the extensive IMAP support in PHP.

---

### Post by 3Miro on 2011-07-03
> **SeijiSensei said:**
> You can write PHP scripts that don't involve the web at all.  You just run them from the command line with "php /path/to/myscript.php".  I've written a number of scripts in PHP to do administrative tasks.  One example is a script that runs nightly which scans all the users' inboxes and archives messages older than a certain date.  In this case I took advantage of the extensive IMAP support in PHP.

I didn't know what, I haven't done PHP in years and back then it was all simple web-based. It is good to know that it is not restricted to the web only.

---

### Post by RiceMonster on 2011-07-03
> **3Miro said:**
> The only "language" that I am unsure about is XML. I think it is borderline programming and it is hard to classify.

XML is consumed by programs themselves for a variety of different purposes, but it cannot make decisions, and it cannot be executed. So no it's not "border line programming", because it's as close as HTML is to programming. It's not hard to classify either. XML - Extensible Markup Language.

---

### Post by 3Miro on 2011-07-03
> **RiceMonster said:**
> XML is consumed by programs themselves for a variety of different purposes, but it cannot make decisions, and **it cannot be executed**. So no it's not "border line programming", because it's as close as HTML is to programming. It's not hard to classify either. XML - Extensible Markup Language.

I can make a C++ program that reads from XML and then acts accordingly. It doesn't take much to make a case statement out of XML:
```

    <IntCases>
        <IntCase>
            <Value>1</Value>
            <WriteString>You entered 1</WriteString>
        </IntCase>
        <IntCase>
            <Value>2</Value>
            <WriteString>You entered 2</WriteString>
        </IntCase>
    </IntCases>

```

Then the C++ program will read this and "execute" it.

Writing the C++ program is programming, but what about the XML part (if I write the C++ part and someone else does the XML). With some creativity I should be able to make my own simple programming language out of XML and C++. Just the way Python has C/C++ part and script Python part, I can make XML-Script language. It will not be useful, but it is doable.

So XML is a borderline language. Although, most of the time it is just used as a markup language.

---

### Post by RiceMonster on 2011-07-03
> **3Miro said:**
> I can make a C++ program that reads from XML and then acts accordingly. It doesn't take much to make a case statement out of XML:
```

    <IntCases>
        <IntCase>
            <Value>1</Value>
            <WriteString>You entered 1</WriteString>
        </IntCase>
        <IntCase>
            <Value>2</Value>
            <WriteString>You entered 2</WriteString>
        </IntCase>
    </IntCases>

```

Then the C++ program will read this and "execute" it.

Writing the C++ program is programming, but what about the XML part (if I write the C++ part and someone else does the XML). With some creativity I should be able to make my own simple programming language out of XML and C++. Just the way Python has C/C++ part and script Python part, I can make XML-Script language. It will not be useful, but it is doable.

So XML is a borderline language. Although, most of the time it is just used as a markup language.

This is your C++ program making a decision and executing based off the XML, not the XML itself doing that. This is no different than having a custom formatted text file and doing the same.

---

### Post by 3Miro on 2011-07-03
> **RiceMonster said:**
> This is your C++ program making a decision and executing based off the XML, not the XML itself doing that. This is no different than having a custom formatted text file and doing the same.

Custom formatted text file that is used by a C++ program to execute commands ... I think this is called a scripting language. You just described Python, which everyone will agree is a programming language.

The issue with XML is that it is incredibly flexible and you can do way more than what you can with HTML. I don't think XML is the same as a programming language, but I think it is way more than a "markup language". Hence, I call XML a borderline thing.

---

### Post by cgroza on 2011-07-03
> **RiceMonster said:**
> This is your C++ program making a decision and executing based off the XML, not the XML itself doing that. This is no different than having a custom formatted text file and doing the same.
Well, python works the same way, it interprets the source file.
He is saying that is possible to create an interpreter for a xml based programming language.

You could even create a compiler, which generates machine code based on the instructions in the XML file.
This could be the syntax of a language like that:
```

<int attr=foo/>
< = var = foo val = 1/>
<switch attr = foo>
     <case attr == 1> <print attr="Hello World"/></case>
</switch>

```

---

### Post by RiceMonster on 2011-07-03
> **cgroza said:**
> Well, python works the same way, it interprets the source file.
He is saying that is possible to create an interpreter for a xml based programming language.

Yes, that's true. However, I still don't consider the possibility to make an interpreted scripting language out it enough to consider it a borderline programming language, in the same way I don't consider a text file a borderline programming language.

---

### Post by cgroza on 2011-07-03
> **RiceMonster said:**
> Yes, that's true. However, I still don't consider the possibility to make an interpreted scripting language out it enough to consider it a borderline programming language, in the same way I don't consider a text file a borderline programming language.
The languages are implemented with a interpreter or a compiler. It is enough for an implementation to exist (Java, Python, Ruby have many implementations available.)

If we create such an implementation, XML could become a programming language.

---

### Post by RiceMonster on 2011-07-03
> **cgroza said:**
> The languages are implemented with a interpreter or a compiler. It is enough for an implementation to exist (Java, Python, Ruby have many implementations available.)

If we create such an implementation, XML could become a programming language.

I didn't deny that.

---

### Post by kevin11951 on 2011-07-03
If XML is a "borderline" scripting language simply because you "could" write an interpreter in C++ to read it and execute what it sees, then anything is a "borderline programming language" by that definition.

Everything from a text file to a spreadsheet can be manipulated and read by C++, in turn you could make a scripting language out of them if you really wanted to...

This does not make them "borderline programming languages".

---

### Post by 3Miro on 2011-07-03
> **RiceMonster said:**
> Yes, that's true. However, I still don't consider the possibility to make an interpreted scripting language out it enough to consider it a borderline programming language, in the same way I don't consider a text file a borderline programming language.

The reason why I brought it up is because I have done something similar (and very basic) with XML, but I see your point too.

If someone makes XML-script and another person is coding in it, then I would call the second person a programmer. Using XML as just a markup language is not programming.

---

### Post by cgroza on 2011-07-03
> **kevin11951 said:**
> If XML is a "borderline" scripting language simply because you "could" write an interpreter in C++ to read it and execute what it sees, then anything is a "borderline programming language" by that definition.

Everything from a text file to a spreadsheet can be manipulated and read by C++, in turn you could make a scripting language out of them if you really wanted to...

This does not make them "borderline programming languages".
Few markup languages have the necessary syntax to make a scripting language.
I do not see how could one interpret a spreadsheet to print a sentence on the screen.

---

### Post by Ctrl-Alt-F1 on 2011-07-03
I'm with RiceMonster on the XML thing. I find it interesting that so many people jumped on the HTML is not programming bandwagon and then said XML is, considering that XML is essentially HTML with custom tags. It can be used for things other than web design, but it just describes a structure and does nothing else.  Your programming language of choice has to decide what to do with that information.

> I do not see how could one interpret a spreadsheet to print a sentence on the screen.
Then you're not trying very hard.

---

### Post by Bandit on 2011-07-03
> **3Miro said:**
> The only "language" that I am unsure about is XML. I think it is borderline programming and it is hard to classify.
Extensible _Markup_ Language, actually HTML is more complex. 

I love using XML to structure my date, XSD to add formatting when needed,  XSLT with CSS to manipulate and display the date. Using HTML in the XSLT file. It sounds overly complicated, but removing all the date from your HTML content lets you actually focus more on the structure of your webpage.

This for example:

**RESUME.XSL**
```
&#65279;<?xml version="1.0" encoding="utf-8" ?>

<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">



<!-- Resume.XSL "Resume CD"                                 -->

<!-- Copyright 2011, Joe Jackson Jr (Exodist2009@gmail.com) -->

<!-- Licensed under the GNU/GPL ver 2.0                     -->



<xsl:output method="html" version="4.0" />

<xsl:template match="/">



<html>

	<head>

	<meta http-equiv="Content-Type" content="text/html" charset="utf-8" />

	<title>Joe Jackson's Resume and Supporting Documentation.</title>

	<link href="resume.css" rel="stylesheet" type="text/css" />

	</head>

	

	<body>

		<table>



		    <tr>   

			<h1><img src="images/header.png" alt="Joe Jackson's Resume and Supporting Documentation CD"/></h1>

			<h2>Resume Package for Magnolia Regional Health Center</h2>

		    </tr>



		   <tr>



		    <hr width="640" align="left" /> 

			<table id="stddoc" cellpadding="0" cellspacing="0"> 

			

			    <tr id="headerformat" cellpadding="0" cellspacing="0" height="0"><img height="48px" src="images/std-sub-header.png" alt="" width="640px" style="vertical-align: bottom; border-style: solid; border-width: 0px"/>

			    </tr>



			    <tr cellpadding="0" cellspacing="0"> 

				<xsl:apply-templates select="documents/item/itemname[../catagoryname='Standard Documents']" />

			    </tr>



			    <tr cellpadding="0" cellspacing="0"><img src="images/sub-footer.png" />

			    </tr>

			    

		       </table>

		

		    <hr width="640" align="left" />

			<table id="supdoc" cellpadding="0" cellspacing="0"> 

			

			    <tr id="headerformat" cellpadding="0" cellspacing="0" height="0"><img src="images/sup-sub-header.png" alt="" height="48px" width="640px" style="vertical-align: bottom; border-style: solid; border-width: 0px"/>

			    </tr>

			

			    <tr cellpadding="0" cellspacing="0">

				<xsl:apply-templates select="documents/item/itemname[../catagoryname='Supporting Documentation']" />

			    </tr>



			    <tr cellpadding="0" cellspacing="0"><img src="images/sub-footer.png" />

			    </tr>



			</table> 

	

			  

		    </tr>

		

		</table>

		

	</body>

</html>



</xsl:template>



<xsl:template match="itemname">

	<table width="640" cellpadding="0" cellspacing="0"  background="images/item-bg.png">	<!-- item-bg moved here for IE fix, Fx still displays correctly, IE still has small gap between subheader and data table. -->

		

		<tr cellpadding="0" cellspacing="0" wdith="100%">

			<td width="100%"> <h3 id="itemnameheader"><xsl:value-of select="." /></h3></td>

		</tr>

				

		<tr cellpadding="0" cellspacing="0">

			<td colspan="2">

				<table width="100%" id="description">

					<tr>

						<td width="54px">

							<img src="images/{../image}"/>

						</td>

						<td id="description" width="100%">

							<xsl:value-of select="../description"/><br />

							<a href="docs/{../link}">Download File</a>

						</td>

					</tr>

					

				</table>

			</td>

		</tr>

				

	</table>



</xsl:template>

</xsl:stylesheet>
```


**RESUME.XML**
```
<?xml version="1.0" encoding="utf-8" ?>

<!-- <?xml-stylesheet type="test/css" href=resume.css?>    -->



<!-- Resume.XML "Resume CD"                                 -->

<!-- Copyright 2011, Joe Jackson Jr (Exodist2009@gmail.com) -->

<!-- Licensed under the GNU/GPL ver 2.0                     -->



<?xml-stylesheet type="text/xsl" href="resume.xsl" ?>



<documents>

				

			<item>

				<catagoryname>Standard Documents</catagoryname>			

				<itemname>Letter of Application</itemname>

				<image>../images/pdf.png</image>

				<description>Document is in PDF Format.</description>

				<link>../docs/LetterOfApplication_MRHC.pdf</link>

			</item>

		

			<item>

				<catagoryname>Standard Documents</catagoryname>			

				<itemname>Resume</itemname>

				<image>../images/pdf.png</image>

				<description>Formated Resume. Document is in PDF Format.</description>

				<link>../docs/Resume_MRHC.pdf</link>

			</item>

			

			<item>

				<catagoryname>Standard Documents</catagoryname>			

				<itemname>Resume Text Version</itemname>

				<image>../images/txt.png</image>

				<description>Document is in standard ASCII Text Format for easy scanning by OCR scanner software. If NotePad doesnt format correctly, please try WordPad.</description>

				<link>../docs/Resume_textversion_MRHC.txt</link>

			</item>	

			

			<item>

				<catagoryname>Standard Documents</catagoryname>			

				<itemname>Reference List</itemname>

				<image>../images/pdf.png</image>

				<description>List of contact information for character references. Document is in PDF Format.</description>

				<link>../docs/ReferenceList.pdf</link>

			</item>	

			

			<item>

				<catagoryname>Supporting Documentation</catagoryname>			

				<itemname>CIW Certification</itemname>

				<image>../images/pdf.png</image>

				<description>Copies of my CIW Web Professional Associate certifications. Documents are in PDF Format.</description>

				<link>../docs/CIW-Certification.pdf</link>

			</item>			

		

			<item>

				<catagoryname>Supporting Documentation</catagoryname>

				<itemname>SK "A" School Certification</itemname>

				<image>../images/image.png</image>

				<description>Copy of my SK "A" School certification from US Naval Supply School in Meridian MS. Document is in PNG Format.</description>

				<link>../docs/SK-A-School-Certification.png</link>

			</item>

			

			<item>

				<catagoryname>Supporting Documentation</catagoryname>

				<itemname>Verification of Training</itemname>

				<image>../images/pdf.png</image>

				<description>This is my Verification of Military Training and Experience. This file list training acquired while in service and responsibility demonstrated by each service rank. Document acquired prior to my separation. Document in PDF Format.</description>

				<link>../docs/VerificationOfMilitaryExperienceAndTraining.pdf</link>

			</item>



</documents>
```

Used with my XSD and CSS files you can get this:

**LOL just realised I need to update my Resume CD.. hehe**

---

### Post by Bandit on 2011-07-03
> **Ctrl-Alt-F1 said:**
> I'm with RiceMonster on the XML thing. I find it interesting that so many people jumped on the HTML is not programming bandwagon and then said XML is, considering that XML is essentially HTML with custom tags. It can be used for things other than web design, but it just describes a structure and does nothing else.  Your programming language of choice has to decide what to do with that information.


Then you're not trying very hard.

Yea Extensible _Markup_ Language is _NOT_ a programming language. I use it religiously. XML is just the standard for data structuring. There are fixed standards for currency, scientific data and so on. But it its self is just tagged data file, no more complex then a filing cabinet.

---

### Post by 1clue on 2011-07-03
Oh come on guys.

XML, HTML and anything similar is markup.  That means it's data.

Another example, a text file is data.  C, for example, is a programming language written in a text file.  While all C files are text files, not all text files contain C.  One of them might contain a letter to your mother.

XML is data.  And, for the record, HTML is a subset of XML.

So you have an XML based source language for programming.  You could do that.  But I could also have valid, well-formed XML which your compiler or interpreter could not convert to any executable machine code.

Yes, an executable computer language could possibly use XML as an input constraint, if you really wanted to make it hard to use and ensure that nobody would use it.  But that doesn't make XML a computer language, it only makes it a container for data.

---

### Post by unknownPoster on 2011-07-03
> **1clue said:**
> 
XML is data.  And, for the record, HTML is a subset of XML.


That's entirely false.

XML and HTML are "siblings." They are both derivatives of SGML.

HTML became a standard in 1995 while the W3C didn't approve XML until 1998.

---

### Post by Bandit on 2011-07-03
> **unknownPoster said:**
> That's entirely false.

XML and HTML are "siblings." They are both derivatives of SGML.

HTML became a standard in 1995 while the W3C didn't approve XML until 1998.

This is true..

---

### Post by 3Miro on 2011-07-03
> **1clue said:**
> Oh come on guys.

XML, HTML and anything similar is markup.  That means it's data.

Another example, a text file is data.  C, for example, is a programming language written in a text file.  While all C files are text files, not all text files contain C.  One of them might contain a letter to your mother.

XML is data.  And, for the record, HTML is a subset of XML.

So you have an XML based source language for programming.  You could do that.  But I could also have valid, well-formed XML which your compiler or interpreter could not convert to any executable machine code.

Yes, an executable computer language could possibly use XML as an input constraint, if you really wanted to make it hard to use and ensure that nobody would use it.  But that doesn't make XML a computer language, it only makes it a container for data.

Your analogy is incorrect. You should not be comparing XML to C, but rather XML to Python.

Both XML and Python come in the form of a formatted text files and they both need an interpreter.

You can have well formatted Python file that fails to execute due to limitations of the interpreter (missing modules).

As you noted, not all XML files can be read by all XML interpreters.

The difference is that Python has one standard interpreter, while XML is used all over the place and for more than one thing. That is why XML is hard to classify.

Traditionally, XML is used to store data, but there are XML interpreters that come close to implementing simple XML-Script. When I think XML I think data AND simple scripting, that is why I made the original note.

Whether or not XML can be called a programming language depends on the specific thing that you do with it.

---

### Post by unknownPoster on 2011-07-03
> **3Miro said:**
> 
Whether or not XML can be called a programming language depends on the specific thing that you do with it.

This is wrong. XML is NOT a programming language. It is a markup language. If XML is a programming language, so is ODF, LaTeX, HTML, etc.

If you want to program with XML, use XSLT. 

[http://en.wikipedia.org/wiki/XSLT](http://en.wikipedia.org/wiki/XSLT)

---

### Post by 3Miro on 2011-07-03
> **unknownPoster said:**
> This is wrong. XML is NOT a programming language. It is a markup language. If XML is a programming language, so is ODF, LaTeX, HTML, etc.


"ODF, LaTeX, HTML, etc" come with specific interpreters and have specific limited tasks.

XML has thousands of interpreters that do completely different things **INCLUDING BASIC SCRIPTING**

This is getting pointless ...

---

### Post by ve4cib on 2011-07-03
> **3Miro said:**
> "ODF, LaTeX, HTML, etc" come with specific interpreters and have specific limited tasks.

XML has thousands of interpreters that do completely different things **INCLUDING BASIC SCRIPTING**

This is getting pointless ...

Actually, LaTeX can be used as a Turing-complete programming language as well.

---

### Post by 3Miro on 2011-07-03
> **ve4cib said:**
> Actually, LaTeX can be used as a Turing-complete programming language as well.

I didn't know that.

So LaTeX is a programming language and the person writing programs on LaTeX should be called a programmer.

---

### Post by 1clue on 2011-07-03
> **unknownPoster said:**
> That's entirely false.

XML and HTML are "siblings." They are both derivatives of SGML.

HTML became a standard in 1995 while the W3C didn't approve XML until 1998.

Not false in the least.  I didn't say anything about "inherited from" or any family tree nonsense.  I said HTML is a ***_subset of_***
XML.  Meaning any structure which exists in HTML can be used verbatim inside of XML, and one could constrain XML such that only valid HTML tags could be used if one should so choose, but a well-formed and valid XML file can contain structures which cannot be in HTML. 

> **3Miro said:**
> Your analogy is incorrect. You should not be comparing XML to C, but rather XML to Python.

Both XML and Python come in the form of a formatted text files and they both need an interpreter.

You can have well formatted Python file that fails to execute due to limitations of the interpreter (missing modules).

As you noted, not all XML files can be read by all XML interpreters.

The difference is that Python has one standard interpreter, while XML is used all over the place and for more than one thing. That is why XML is hard to classify.

Traditionally, XML is used to store data, but there are XML interpreters that come close to implementing simple XML-Script. When I think XML I think data AND simple scripting, that is why I made the original note.

Whether or not XML can be called a programming language depends on the specific thing that you do with it.

My analogy is fine, your understanding is lacking.  And I did not say that not all XML parsers can read all XML.  The exact opposite is true, if you have a compliant XML parser then it can read any XML document and extract relevant information from it.  By definition.  That's the point.

Where is the machine instruction which sets my first name to Bob and my last name to Jones?  XML is data.  You're saying that because it's a structured text file then it must inherently be a programming language.  That's entirely false.  A job application is structured text.  It is not a computer program.  You may as well draw the line in the sand way over to the left and say that since it contains character data it must be a computer programming language.

C is not in a structured text file, it's free form.  C is undoubtedly a computer programming language.  One could also embed C in XML if you wished to, but there would be no point to do so that I can think of.

XML is entirely unrelated to computer programming languages.  Comparing programming languages to HTML/XML/whatever is akin to comparing a screwdriver and a dog.  XML is an attempt to organize free-form text ***_data_*** such that any compliant parser can read it, without reliance on a proprietary tool.

Should you choose to do so you could cause an interpreter or compiler to parse XML into something executable, but as far as the XML parser is concerned it's just data.  And as far as that goes, a computer programming language and XML are at odds with each other.

The computer programming language is supposed to make a simple, easy-to-read file that allows humans to tell the computer what to do.

The XML file is supposed to allow a computer to read a text file and reach the desired data without significant chance of mistakes.

---

### Post by 3Miro on 2011-07-03
> **1clue said:**
> 
My analogy is fine, your understanding is lacking.  And I did not say that not all XML parsers can read all XML.  The exact opposite is true, if you have a compliant XML parser then it can read any XML document and extract relevant information from it.  By definition.  That's the point.

Where is the machine instruction which sets my first name to Bob and my last name to Jones?  XML is data.  You're saying that because it's a structured text file then it must inherently be a programming language.  That's entirely false.  A job application is structured text.  It is not a computer program.  You may as well draw the line in the sand way over to the left and say that since it contains character data it must be a computer programming language.

C is not in a structured text file, it's free form.  C is undoubtedly a computer programming language.  One could also embed C in XML if you wished to, but there would be no point to do so that I can think of.

XML is entirely unrelated to computer programming languages.  Comparing programming languages to HTML/XML/whatever is akin to comparing a screwdriver and a dog.  XML is an attempt to organize free-form text ***_data_*** such that any compliant parser can read it, without reliance on a proprietary tool.

Should you choose to do so you could cause an interpreter or compiler to parse XML into something executable, but as far as the XML parser is concerned it's just data.  And as far as that goes, a computer programming language and XML are at odds with each other.


As I said again, most of the objections that you make against XML being a programming language can be aimed at Python as well. Where are the machine instructions in Python? Or would you say that Python is not a programming language?

XML is used in more than just browsers and many XML interpreters will not be able to handle well formatted XML files. Most XML interpreters work with special set of tags and will fail to recognize anything outside of those.

HTML is a subset of XML only in browsers (as browsers already know HTML). Try HTML tags in something like hald or OpenBox settings files. Just be careful as those will crash your system.

> 
The computer programming language is supposed to make a simple, easy-to-read file that allows humans to tell the computer what to do.


XML can do that and in some rare occasions does exactly that.

> 
The XML file is supposed to allow a computer to read a text file and reach the desired data without significant chance of mistakes.

This is only the traditional and most common use of XML.

I don't want to call XML a "programming language", I want to point out that there are more nuances than a simple a language vs not a language. I call XML borderline thing.

---

### Post by Spr0k3t on 2011-07-03
Just the other day I was thinking about this.  HTML coupled with XML and CSS is still nothing more than just markup.  Now, the instant you start throwing AJAX around with those three, you have a programming language... but AJAX is essentially using an extension of the DOM through the use of background XML components and JavaScript.  The fact remains that CSS is not HTML, neither is JavaScript or XML... HTML is a separate entity of it's own.

If the code is interpreted (meaning different for each static display based on environment criteria) it could be considered a programming language.  Remove any element of layout, publishing, or art from HTML and what do you have left?  That's right, nothing.  So no... it can't be a programming language.

HTML can not evaluate the expression of a string of numbers and bit operators without the use of some external logic controller.

---

### Post by wojox on 2011-07-03
No, HTML is not a programming language. It is a Markup or Container language. 

I don't think I need to give reasons as they seem to be all covered here. ;)

---

### Post by red_Marvin on 2011-07-03
It is likely possible to create an interpreter that can take basically
[i]any[i] well-formed XML document and interpret it as a source file.

Case in point; It should be possible to do a depth-first traversal
of the tree and map the tags onto brainf*** instructions based on some
arbitrary rule like character count mod 4 etc.
[size=1](Brainf*** is a bit extreme but simple to create a mapping rule for,
and since it is turing complete it proves the point.)[/size]

I would argue that the ponts so far expressing that XML is a programming
language boils down to the above example in one way or another.

The above example does not, however, prove that XML is a programming language.
Why? because there is nothing in the XML specification describing
this kind of interpretation of the XML document, neither is there any
description of the semantics of 3Miro's example in post [13](http://ubuntuforums.org/showpost.php?p=11007998&postcount=13) in
the XML spec. Adding *that* would make it a programming language,
but then it would be more than just XML.

All XML deals with is the tree data structure, nothing else.

---

### Post by 3Miro on 2011-07-03
> **red_Marvin said:**
> It is likely possible to create an interpreter that can take basically
[i]any[i] well-formed XML document and interpret it as a source file.

Case in point; It should be possible to do a depth-first traversal
of the tree and map the tags onto brainf*** instructions based on some
arbitrary rule like character count mod 4 etc.
[size=1](Brainf*** is a bit extreme but simple to create a mapping rule for,
and since it is turing complete it proves the point.)[/size]

I would argue that the ponts so far expressing that XML is a programming
language boils down to the above example in one way or another.


Brainf*** is an extreme example, but it is valid. Creating XML-Script is viable.

> 
The above example does not, however, prove that XML is a programming language.
Why? because there is nothing in the XML specification describing
this kind of interpretation of the XML document, neither is there any
description of the semantics of 3Miro's example in post [13](http://ubuntuforums.org/showpost.php?p=11007998&postcount=13) in
the XML spec. Adding *that* would make it a programming language,
but then it would be more than just XML.


I would give you that, I have no trouble saying that XML is not a programming language, but it is incorrect to claim that it is just a markup language either (not that you are making that claim).

> 
All XML deals with is the tree data structure, nothing else.
Absolutely true.

IIRK any computer language can be represented by a gigantic three structure. XML may be lesser than Python as it does not come with an interpreter, however, XML is way more than HTML and it is wrong to claim they are the same.

XML is hard to classify, which way my point this entire time.

---

### Post by 1clue on 2011-07-03
> **3Miro said:**
> As I said again, most of the objections that you make against XML being a programming language can be aimed at Python as well. Where are the machine instructions in Python? Or would you say that Python is not a programming language?


I personally don't have much use for Python, but it is a language which is designed to be executed.  XML is designed as markup, which means it is designed to hold data.

> 
XML is used in more than just browsers and many XML interpreters will not be able to handle well formatted XML files. Most XML interpreters work with special set of tags and will fail to recognize anything outside of those.


That it's used in browsers is only of mild interest to me.  My company uses it extensively, and we design our own documents, and we use standard parsers because (1) they can read any document and (2) why re-invent the wheel?

Any document that can't be read by a standard, complete XML parser is not XML.  The language is extensible (by definition and name) but there are rules that need to be followed.

There are thousands of parsers out there that were cooked together for a specific purpose, and then modified to fit whatever needs the company had at the time.  I wrote one of them.  Then we realized that the standard parsers can do it faster, more reliably and most of all without my having to code them, so we happily ditched what I came up with.

> 
HTML is a subset of XML only in browsers (as browsers already know HTML). Try HTML tags in something like hald or OpenBox settings files. Just be careful as those will crash your system.


This is false.  XML is XML, and its flexibility is designed into the language.  You can use any tag you want, and as long as you have a matching closing tag like this:
     <table>
     ...
     </table>

Or a leaf tag like this:
     <br/>

you have broken no rules by using that tag.

HTML is almost never used outside of a browser, but we use it to generate PDFs on a server, without the presence of a browser so it can be done.

> 
XML can do that and in some rare occasions does exactly that.


You can also drive a bulldozer down the freeway, but that doesn't mean you would want to do so.  You can drive screws with a hammer, but that doesn't mean that a hammer is a screwdriver.

> 
I don't want to call XML a "programming language", I want to point out that there are more nuances than a simple a language vs not a language. I call XML borderline thing.

You could write C code to store your addresses and then require that it be compiled and executed in order to get the data out, but why would you want to?  That doesn't turn C into a database, even though you're storing data in it.

---

### Post by red_Marvin on 2011-07-03
> **3Miro said:**
> ...but it is incorrect to claim that it is just a markup language either. [...another quote...] Absolutely true.
You agree that XML does only describes a tree data structure, but not that it is only a markup language? Could you elaborate on this?

Also I was not targetting you specifically, just that you provided another
example of mapping XML tags to program execution in a more obvious manner
than the brainf***.

---

### Post by 3Miro on 2011-07-03
> **1clue said:**
> I personally don't have much use for Python, but it is a language which is designed to be executed.  XML is designed as markup, which means it is designed to hold data.

See previous post about tree structures.

> 
Any document that can't be read by a standard, complete XML parser is not XML.  The language is extensible (by definition and name) but there are rules that need to be followed.


Are you saying that OpenBox doesn't use XML. I am pretty sure OpenBox wouldn't know what the <table> tag is not would it know how to handle it.

There is a difference between reading the data and working with it. When I say "parser" I mean something that actually uses the data. I can open any text file with Gedit, but I don't have a Python file until I can open it with the python interpreter.

You seem to call XML just the tree data. But then a Python script is also just a text file. XML is the file + the program using it, just like Python is the file + the Python interpreter itself.

I think the above is the main disagreement that we have.

> 
There are thousands of parsers out there that were cooked together for a specific purpose, and then modified to fit whatever needs the company had at the time.  I wrote one of them.  Then we realized that the standard parsers can do it faster, more reliably and most of all without my having to code them, so we happily ditched what I came up with.


I had a bunch of XML data and I wanted to let the user write simple if statements regarding relations between this data and other data that I got in real time. I could have coupled the C++ code with something like Python, but it was easier to just add the "if" statements as part of the XML. Then I had a C++ program that would read the whole thing and work with it.

You cannot do that with HTML as every tag is clearly specified and you cannot add your own. XML is way more than HTML.

> 
This is false.  XML is XML, and its flexibility is designed into the language.  You can use any tag you want, and as long as you have a matching closing tag like this:
     <table>
     ...
     </table>

Or a leaf tag like this:
     <br/>

you have broken no rules by using that tag.

I will try this in OpenBox, just out of curiosity, but I am pretty sure it will crash on the <table> tag.

> 
You can also drive a bulldozer down the freeway, but that doesn't mean you would want to do so.  You can drive screws with a hammer, but that doesn't mean that a hammer is a screwdriver.

You could write C code to store your addresses and then require that it be compiled and executed in order to get the data out, but why would you want to?  That doesn't turn C into a database, even though you're storing data in it.

People do use XML as a programming language. This is not designed by default nor is it used often, but it works. Thus XML is not clearly one side of the line or the other, unlike C and HTML it is hard to classify.

---

### Post by red_Marvin on 2011-07-03
> **3Miro said:**
> You seem to call XML just the three data. But then a Python script is also just a text file. XML is the file + the program using it, just like Python is the file + the Python interpreter itself.

I think the above is the main disagreement that we have.

Python is a programming language since it defines syntax and semantics
for interpreting the source into something executable.

XML has syntax and semantics for interpreting it into a tree structure
of data, which in order to be executable requires additional semantics that
are outside the scope of XML. So XML is not a programming language,
because it only takes us to the tree.

---

### Post by 3Miro on 2011-07-03
> **red_Marvin said:**
> You agree that XML does only describe a tree data structure, but not that it is only a markup language? Could you elaborate on this?


A computer language is a tree data structure, is it not? You can write it in a markup format or not, but it is a tree.

HTML has very specific use, it does document formatting. HTML by itself is useless, it is always used in conjunction with a browser or pdf viewer or something of that sort.

XML doesn't have a default interpreter (I guess my disagreement with 1clue comes exactly in the definition of "interpreter"). Coupled with the right interpreter, XML can and sometimes is used as a programming language.

XML isn't the same as Python, but it is a lot more than HTML.

---

### Post by cgroza on 2011-07-03
> **red_Marvin said:**
> Python is a programming language since it defines syntax and semantics
for interpreting the source into something executable.

XML has syntax and semantics for interpreting it into a tree structure
of data, which in order to be executable requires additional semantics that
are outside the scope of XML. So XML is not a programming language,
because it only takes us to the tree.
I assure you that XML syntax and semantics are suitable and expressive enough to support a implementation similar to interpreted languages and even compiled.

Let's take ruby as an example. The standard implementation does not generate bytecode, instead it generates an internal tree that was parsed from the source files.

In the end, program are just trees of instructions that are followed accordingly to the decisions taken by the program.

---

### Post by red_Marvin on 2011-07-03
3Miro:
I think we are using different words here, when I say markup I don't mean anything to do with HTML, markup is just a declaration of structure and content ([wikipedia on markup language](http://en.wikipedia.org/wiki/Markup_language))
such as a tree structure. I think this is what you actually mean with "computer language"

---

### Post by 3Miro on 2011-07-03
> **red_Marvin said:**
> 3Miro:
I think we are using different words here, when I say markup I don't mean anything to do with HTML, markup is just a declaration of structure and content ([url=
http://en.wikipedia.org/wiki/Markup_language]wikipedia on markup language[/url])
such as a tree structure. I think this is what you actually mean with "computer language"

When I say "markup", I mean tags. Apparently according to Wikipedia this is incorrect.

They do list LaTeX as an example of a Markup Language, however, someone earlier in the thread noted that LaTeX is a programming language in the executable sense (i.e. you can apparently make an executable). According to this, the distinction between "Markup Language" and a "Programming Language" is even murkier.

PS It was ve4cib on post #32.

---

### Post by red_Marvin on 2011-07-03
> **cgroza said:**
> I assure you that XML syntax and semantics are suitable and expressive enough to support a implementation similar to interpreted languages and even compiled.

Let's take ruby as an example. The standard implementation does not generate bytecode, instead it generates an internal tree that was parsed from the source files.

In the end, program are just trees of instructions that are followed accordingly to the decisions taken by the program.

My point is that while almost any programming language, can be parsed
into a tree structure they are programming languages because they
interpret the nodes of the tree as executable statements or data or
whatever.

XML does NOT take us further than the tree structure. Whatever happens
after the XML source has been parsed into a tree by the XML parser is
NOT part of what XML is.

---

### Post by cgroza on 2011-07-03
> **red_Marvin said:**
> My point is that while almost any programming language, can be parsed
into a tree structure they are programming languages because they
interpret the nodes of the tree as executable statements or data or
whatever.

XML does NOT take us further than the tree structure. Whatever happens
after the XML source has been parsed into a tree by the XML parser is
NOT part of what XML is.
XML is just a set of rules and specification, just like python, Ruby, Java, C++.  There are implementations that follow those rules.
Python (CPython, Jython) [Python has many more]
Ruby (MRI, IronRuby)
Java (Sun Java, OpenJdk)
C++ (any C++ compiler)

 An interpreter can follow the rules and use the rules as the language's syntax and generate/interpret/execute the code.

So an implementation of XML (say XMLscript) can be built to do the exact same thing as the above.

---

### Post by 3Miro on 2011-07-03
> **red_Marvin said:**
> My point is that while almost any programming language, can be parsed
into a tree structure they are programming languages because they
interpret the nodes of the tree as executable statements or data or
whatever.

XML does NOT take us further than the tree structure. Whatever happens
after the XML source has been parsed into a tree by the XML parser is
NOT part of what XML is.

The Python language is useless without a python interpreter and HTML is useless without a browser. In the same way XML is useless without some interpreter.

The first 2 have a general focus, the last one doesn't. XML could go the way of HTML or the way of Python or some combination of both. Hence I claim that XML is hard to classify in one of the two boxes (programming/not programming) and I guess this is the source of the disagreement.

Since this no longer relates to the original post, I don't thing there is any point in arguing further.

---

### Post by 1clue on 2011-07-03
> **3Miro said:**
> See previous post about tree structures.

Are you saying that OpenBox doesn't use XML. I am pretty sure OpenBox wouldn't know what the <table> tag is not would it know how to handle it.

There is a difference between reading the data and working with it. When I say "parser" I mean something that actually uses the data. I can open any text file with Gedit, but I don't have a Python file until I can open it with the python interpreter.


We have a serious problem with vocabulary.  [http://www.programmar.com/parser.htm](http://www.programmar.com/parser.htm)

A parser breaks data (not necessarily even text) into smaller parts based on rules.  It makes absolutely no analysis of that data, other than to break it down correctly.

Whether OpenBox has anything that can understand a table element has absolutely nothing to do with it.  The parser that OpenBox uses can read the entire file, and the software examining that data can fuss over a table tag or ignore it as it so chooses.

You need to spend some time reading specifications.  The XML spec states that, as long as the file is well-formed and valid, the application should not error over tags it has no understanding of, especially if namespaces are involved.  XML allows multiple applications to use the same file for configuration, and if your program freaks every time it sees something it can't understand this approach would be impossible.

[http://www.w3.org/standards/xml/](http://www.w3.org/standards/xml/)

> 
You seem to call XML just the tree data. But then a Python script is also just a text file. XML is the file + the program using it, just like Python is the file + the Python interpreter itself.

I think the above is the main disagreement that we have.


Then your definitions are counter to the definitions of W3C.

The spec covers standard syntax, definition files, schemas, searching and rules for transforming based on styles.  It does not dictate specific processes for interpretation of the data.

The entire point of XML is that the exchange of data should not depend on any single external component.  We can and I have swapped one XML parser out for another, without changing anything else, and without any problems.

If you properly constrain the XML then you can even use a standard XML editor to get an editing screen to populate the file.  Or later use a style sheet so you can use a web browser to do it.

People go through all sorts of unnecessary crap to "use XML."  That defeats the purpose of XML altogether.  Focus on what you want to get out of the file, or write to it, and pick an implementation of a standard tool to handle the rest.  Try it, you'll like it.

---

### Post by 1clue on 2011-07-03
Pardon the double post, but in re-reading the previous post I realized something else.

A modern computer programming language is not defined by what the compiler gives you for error messages.  It's defined by a specification.  The quality of any given compiler/interpreter is judged by the behavior of that compiler/interpreter in compiling certain test code, and in the results of executing that code.

For that matter, I know of no compiler which is 100% compliant with any language spec.  Every vendor ignores some things and adds others as they feel add a little something to the mix.  Some of those things make it into the language spec later.

---

### Post by 3Miro on 2011-07-03
You are right that I don't use the proper terminology and it did cause confusion.

The issue is that you look at XML as just something to store data. Under that definition the only difference between the XML file and a regular text file with the same data written in Python is the formatting.

In Python you call an external program to either read the data or "execute" the data. You can do the same with the XML.

Note that you cannot do this with regular HTML. Although you can apparently do it with other mark-up languages like LaTeX.

I claim that XML is more than HTML as it does allow for execution. You disagree saying that "execution" is not part of the XML.

As this is unrelated to the original post, I think further discussion is pointless.

PS Cross post with your second post. I only have to add that I agree that people should follow specifications, but under this, many programs that claim to use XML would actually fail. This makes our disagreement even more pointless as we are talking about different things altogether.

---

### Post by ve4cib on 2011-07-03
> **3Miro said:**
> I didn't know that.

So LaTeX is a programming language and the person writing programs on LaTeX should be called a programmer.

LaTeX is a typesetting language that can contain executable, Turing-complete code.  Most people don't do any programming in LaTeX, but it's possible to do.

I think it would be more correct to say that someone using LaTeX *could* be called a programmer, depending on what they are using LaTeX for.  Most people who use LaTeX to write reports, articles, and whatnot are only using it as a markup language, and thus wouldn't be considered "programmers" in my books.

---

### Post by Bandit on 2011-07-03
What the heck is all this craziness going on here about XML, XSLT, XSD and CSS. I thought I made this perfectly clear two dozen post back. 

**XML**, _Extensible Markup Language_ is a Markup language for STRUCTURING data within tags.
**XSLT** uses HTML markups within it to offer display formatting of the data from the parent XML file. Although called a XML style sheet its not like a CSS, it just displays the data from the XML file like a normal HTML file would.
**XSD**, manipulates how the data information within XML is to be formated, like turning the word TIME to time or Time, or the format of currency from 1000 to 1,000 or $1,000.00. 
**CSS** is the the style sheet.


_***NON THESE ARE PROGRAMMING LANGUAGES***_
I hope I am crystal clear on this, I like to call myself pretty adept to using XML for many years now as its my favourite markup language and I have had multiple college courses in regards to it which I all got As in.

---

### Post by 1clue on 2011-07-03
But now you're finally making sense.

XML parsers have a callback mechanism to allow for dynamic, sequential setting of values or handling of the data, but that doesn't make it executable.  It's more along the lines of standing by a conveyor belt and pulling out the carrots for your basket but leaving the apples.

Yes, that could allow for some sort of execution done by the listener, but it's not a programming language.

A programming language *facilitates* execution.  XML *facilitates* data retrieval.  If you were to actually read the specs (not just 3Miro but everyone who persists on calling XML a programming language) you would realize what a huge pain in the rear it would be to actually develop executable code that way.  In the purely technical sense you COULD make an executable language based on XML input, but it would be one of the most obnoxious languages ever made.

---

### Post by Bandit on 2011-07-03
> **3Miro said:**
> You are right that I don't use the proper terminology and it did cause confusion.

The issue is that you look at XML as just something to store data. Under that definition the only difference between the XML file and a regular text file with the same data written in Python is the formatting.

In Python you call an external program to either read the data or "execute" the data. You can do the same with the XML.

Note that you cannot do this with regular HTML. Although you can apparently do it with other mark-up languages like LaTeX.

I claim that XML is more than HTML as it does allow for execution. You disagree saying that "execution" is not part of the XML.

As this is unrelated to the original post, I think further discussion is pointless.

PS Cross post with your second post. I only have to add that I agree that people should follow specifications, but under this, many programs that claim to use XML would actually fail. This makes our disagreement even more pointless as we are talking about different things altogether.

What is the EXECUTION you guys are talking about??

You can open the file and most browsers will display it. When used in conjunction with XSLT it can be used to display data like a HTML Website as I shown before. But it can not execute any code, its strictly static and can not changed based on any variables.

---

### Post by unknownPoster on 2011-07-03
> **Bandit said:**
> What the heck is all this craziness going on here about XML, XSLT, XSD and CSS. I thought I made this perfectly clear two dozen post back. 

**XML**, _Extensible Markup Language_ is a Markup language for STRUCTURING data within tags.
**XSLT** uses HTML markups within it to offer display formatting of the data from the parent XML file. Although called a XML style sheet its not like a CSS, it just displays the data from the XML file like a normal HTML file would.
**XSD**, manipulates how the data information within XML is to be formated, like turning the word TIME to time or Time, or the format of currency from 1000 to 1,000 or $1,000.00. 
**CSS** is the the style sheet.


_***NON THESE ARE PROGRAMMING LANGUAGES***_
I hope I am crystal clear on this, I like to call myself pretty adept to using XML for many years now as its my favourite markup language and I have had multiple college courses in regards to it which I all got As in.

XSLT IS a programming language as it is Turing Complete. To deny that it is a programming language is to deny Turing Completeness.

---

### Post by Bandit on 2011-07-03
> **1clue said:**
> But now you're finally making sense.

XML parsers have a callback mechanism to allow for dynamic, sequential setting of values or handling of the data, but that doesn't make it executable.  It's more along the lines of standing by a conveyor belt and pulling out the carrots for your basket but leaving the apples.

Yes, that could allow for some sort of execution done by the listener, but it's not a programming language.

A programming language *facilitates* execution.  XML *facilitates* data retrieval.  If you were to actually read the specs (not just 3Miro but everyone who persists on calling XML a programming language) you would realize what a huge pain in the rear it would be to actually develop executable code that way.  In the purely technical sense you COULD make an executable language based on XML input, but it would be one of the most obnoxious languages ever made.

This is true here.

Also you can use other OOP Languages like C++ or even some scripting ones like PHP or Javascript to pull data from the XML file to be used in the program. Matter of fact using Javascript and XML is common place and called [AJAX]("http://en.wikipedia.org/wiki/Ajax_%28programming%29").

---

### Post by Bandit on 2011-07-03
> **unknownPoster said:**
> XSLT IS a programming language as it is Turing Complete. To deny that it is a programming language is to deny Turing Completeness.

XSLT is NOT a programming language no more the HTML. To claim so is complete heresy. I am fluid in using XSL and I tell you its NOT a programming language.

---

### Post by unknownPoster on 2011-07-03
> **Bandit said:**
> XSLT is NOT a programming language no more the HTML. To claim so is complete heresy. I am fluid in using XSL and I tell you its NOT a programming language.

This statement just shows your inexperience with programming languages in general. I'm done with this as you seem to ignore facts.

---

### Post by Bandit on 2011-07-03
> **unknownPoster said:**
> This statement just shows your inexperience with programming languages in general. I'm done with this as you seem to ignore facts.

LOL if I ignored the facts I would have never passed my CIW or passed my XML courses at the top of my class.

This here is about as complexe as XSLT comes, if you can find a IF or any other logic statements in this file I will shake your hand.

```
&#65279;<?xml version="1.0" encoding="utf-8" ?>

<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">



<!-- Resume.XSL "Resume CD"                                 -->

<!-- Copyright 2011, Joe Jackson Jr (Exodist2009@gmail.com) -->

<!-- Licensed under the GNU/GPL ver 2.0                     -->



<xsl:output method="html" version="4.0" />

<xsl:template match="/">



<html>

	<head>

	<meta http-equiv="Content-Type" content="text/html" charset="utf-8" />

	<title>Joe Jackson's Resume and Supporting Documentation.</title>

	<link href="resume.css" rel="stylesheet" type="text/css" />

	</head>

	

	<body>

		<table>



		    <tr>   

			<h1><img src="images/header.png" alt="Joe Jackson's Resume and Supporting Documentation CD"/></h1>

			<h2>Resume Package for Magnolia Regional Health Center</h2>

		    </tr>



		   <tr>



		    <hr width="640" align="left" /> 

			<table id="stddoc" cellpadding="0" cellspacing="0"> 

			

			    <tr id="headerformat" cellpadding="0" cellspacing="0" height="0"><img height="48px" src="images/std-sub-header.png" alt="" width="640px" style="vertical-align: bottom; border-style: solid; border-width: 0px"/>

			    </tr>



			    <tr cellpadding="0" cellspacing="0"> 

				<xsl:apply-templates select="documents/item/itemname[../catagoryname='Standard Documents']" />

			    </tr>



			    <tr cellpadding="0" cellspacing="0"><img src="images/sub-footer.png" />

			    </tr>

			    

		       </table>

		

		    <hr width="640" align="left" />

			<table id="supdoc" cellpadding="0" cellspacing="0"> 

			

			    <tr id="headerformat" cellpadding="0" cellspacing="0" height="0"><img src="images/sup-sub-header.png" alt="" height="48px" width="640px" style="vertical-align: bottom; border-style: solid; border-width: 0px"/>

			    </tr>

			

			    <tr cellpadding="0" cellspacing="0">

				<xsl:apply-templates select="documents/item/itemname[../catagoryname='Supporting Documentation']" />

			    </tr>



			    <tr cellpadding="0" cellspacing="0"><img src="images/sub-footer.png" />

			    </tr>



			</table> 

	

			  

		    </tr>

		

		</table>

		

	</body>

</html>



</xsl:template>



<xsl:template match="itemname">

	<table width="640" cellpadding="0" cellspacing="0"  background="images/item-bg.png">	<!-- item-bg moved here for IE fix, Fx still displays correctly, IE still has small gap between subheader and data table. -->

		

		<tr cellpadding="0" cellspacing="0" wdith="100%">

			<td width="100%"> <h3 id="itemnameheader"><xsl:value-of select="." /></h3></td>

		</tr>

				

		<tr cellpadding="0" cellspacing="0">

			<td colspan="2">

				<table width="100%" id="description">

					<tr>

						<td width="54px">

							<img src="images/{../image}"/>

						</td>

						<td id="description" width="100%">

							<xsl:value-of select="../description"/><br />

							<a href="docs/{../link}">Download File</a>

						</td>

					</tr>

					

				</table>

			</td>

		</tr>

				

	</table>



</xsl:template>

</xsl:stylesheet>
```

---

### Post by Dustin2128 on 2011-07-03
OP was talking about HTML, not XML. Anyway, computer language yes, programming language no.

---

### Post by 3Miro on 2011-07-03
> **1clue said:**
> But now you're finally making sense.

XML parsers have a callback mechanism to allow for dynamic, sequential setting of values or handling of the data, but that doesn't make it executable.  It's more along the lines of standing by a conveyor belt and pulling out the carrots for your basket but leaving the apples.

Yes, that could allow for some sort of execution done by the listener, but it's not a programming language.

A programming language *facilitates* execution.  XML *facilitates* data retrieval.  If you were to actually read the specs (not just 3Miro but everyone who persists on calling XML a programming language) you would realize what a huge pain in the rear it would be to actually develop executable code that way.  In the purely technical sense you COULD make an executable language based on XML input, but it would be one of the most obnoxious languages ever made.

Ah, now we are getting somewhere.

> Yes, that could allow for some sort of execution done by the listener, but it's not a programming language.

Actually this is exactly how Python works. Data from the file is read on the fly and the "listener" or python interpreter executes code based on the data. It is just more efficient than what XML-Script would be.

I think I should restate my earlier position. When we call someone a programmer, I think we should look into what they do as opposed to what are they using.

A person who uses C++, but only edits hard-coded data arrays would not be doing programming.

A person who uses XML-Script would be doing obnoxious programming, but programming nevertheless.

---

### Post by Fluff Blue on 2011-07-03
If you ask me, anything that is scripted or interpreted is not programming.  This list includes: CSS, JavaScript, HTML, PHP, XML, XHTML, or Drag-n-drop languages (GameMaker, some versions of Turtle).

Sorry, friend.

---

### Post by 3Miro on 2011-07-03
> **Fluff Blue said:**
> If you ask me, anything that is scripted or interpreted is not programming.  This list includes: CSS, JavaScript, HTML, PHP, XML, XHTML, or Drag-n-drop languages (GameMaker, some versions of Turtle).

Sorry, friend.

What about Java?

---

### Post by ve4cib on 2011-07-03
> **Fluff Blue said:**
> If you ask me, anything that is scripted or interpreted is not programming.  This list includes: CSS, JavaScript, HTML, PHP, XML, XHTML, or Drag-n-drop languages (GameMaker, some versions of Turtle).

Sorry, friend.

So Python, Lisp, Prolog, Perl, Bash, and FP, among countless others, are not programming languages either?  And what about JIT-compiled/byte-compiled languages like Java and C#?

You sir, have a very rigid definition of "programming" to say the least.

---

### Post by Bandit on 2011-07-03
> **Fluff Blue said:**
> If you ask me, anything that is scripted or interpreted is not programming.  This list includes: CSS, JavaScript, HTML, PHP, XML, XHTML, or Drag-n-drop languages (GameMaker, some versions of Turtle).

Sorry, friend.

What defines as a [programming language]("http://en.wikipedia.org/wiki/Programming_language") is any code that can be used to do calculations based upon the data given, weather it be numbers for a integer operation or a mix of numbers or letters in the string operation. Doesnt matter if it requires compiling or an interpreter.

---

### Post by Dustin2128 on 2011-07-03
> **Fluff Blue said:**
> If you ask me, anything that is scripted or interpreted is not programming.  This list includes: CSS, JavaScript, HTML, PHP, XML, XHTML, or Drag-n-drop languages (GameMaker, some versions of Turtle).

Sorry, friend.
PHP not a programming language? I think you are seriously misinformed as to what constitutes a programming language. Java, python, perl and lisp are all interpreted too (though some can be compiled).

---

### Post by Bandit on 2011-07-03
I am thinking Fluffblue hasnt really seen modern scripting languages. They are a lot more advanced then DOS batch files. :D

---

### Post by Dustin2128 on 2011-07-03
> **Bandit said:**
> I am thinking Fluffblue hasnt really seen modern scripting languages. They are a lot more advanced then DOS batch files. :D
Even then
[QUOTE=wikipedia- scripting language]A **scripting language**, **script language** or **extension language** is a [programming language]("http://en.wikipedia.org/wiki/Programming_language") that...[/QUOTE]

---

### Post by Bandit on 2011-07-03
> **Dustin2128 said:**
> Even then

Very true. Today its hard to find a scripting language that isnt a programming language.

---

### Post by 1clue on 2011-07-04
> **3Miro said:**
> Actually this is exactly how Python works. Data from the file is read on the fly and the "listener" or python interpreter executes code based on the data. It is just more efficient than what XML-Script would be.

I think I should restate my earlier position. When we call someone a programmer, I think we should look into what they do as opposed to what are they using.

A person who uses C++, but only edits hard-coded data arrays would not be doing programming.

A person who uses XML-Script would be doing obnoxious programming, but programming nevertheless.

Actually that's the way absolutely every event-driven model works, programming language or not, or whether it's on a computer or not.  So responding to events does not make it a programming language, it just allows some sort of predictable cause and effect relationship.  Which you can find inside of a wind-up clock made hundreds of years ago.

You guys are totally missing the point here.  You're trying to thread a needle with a bulldozer, and while it might actually be possible it's about the least likely approach.  Speaking as somebody who has built a lot of code around this "event" model we're talking about for XML parsers, it's a whole lot easier to use a real language.  In fact I would say it's probably a lot easier to start from scratch and make your whole interpreter/compiler than to try to adapt the XML callback to make it into a useful language.

I'm also uncomfortable with calling somebody a programmer or not because they managed to make a computer print out "hello world" or similar.  A programmer is someone who brings into existence an application which performs some sort of useful task.  A professional programmer is one who can do so on time and under budget, consistently.

Re:  XSLT.  It is in no way a programming language.  It's a data map that tells some intelligent software how to convert data from one format into another.

Re:  interpreted languages not being programming languages.  ********.  Since people started using computers to convert human-readable programming languages into machine-executable code, there have been interpreters and those interpreters have done real work.  I'm unaware of any computer currently on the market except appliances that don't use some sort of scripting language as a key component to their operation.

For that matter, if you're running Ubuntu you won't boot without a scripting language playing a significant role.

Re:  Java.  Java is not only a programming language, it's a hardware spec, a virtual machine and an operating environment on which literally hundreds of languages can be used to generate executable Java bytecode.  If your company uses off-the-shelf accounting software, then there is an extremely high chance that you are using Java.  If you watch Blu-Ray, then you are using Java.  It is definitely not appropriate for everything, but where it is appropriate it does well.

---

### Post by johnnybelfast on 2011-07-04
I would argue that it could be classed as an interpreted programming language, where the browser is the interpreter, the html is the code and the website's functions make up the application. IF you look at chromeos the browser is actually part of the OS and the applications are all html based ( probably with some php/asp/perl/jsp/javascript etc supporting them)

It would also fit under the definition of a script, a markup language etc. I guess HTML falls under many categories. I would never criticise anyone who claimed to program html, it's just another level of programming in my eyes.


I would also argue that XSLT is a programming language and tools like FOP are compilers which compile the script (even assembly language is a script) and data into a software readable binary format (PDF). I use XSLT and FOP at work to generate mail-merged PDF statements which go to over 1 million people. Two of the scripts I use work out automatically whether each statement is A4 single, a4 duplex, A3 single, A3 duplex or A4 multi, so it can be output to the necessary PDF file. It takes about 40 minutes to generate the PDF's and then I need to split them so that the printers can handle them efficiently. Not many people know how to do that, especially with XSLT. 

To me writing computer code is programming, no matter how high or low the level is... That's what programming has always been. Punching in computer readable commands to generate a specific output one way or another. Once upon a time that was done on cards with holes in them.

Check out the history of programming on the ever reliable (jk) Wikipedia: [http://en.wikipedia.org/wiki/Computer_programming#History](http://en.wikipedia.org/wiki/Computer_programming#History)

---

### Post by DangerOnTheRanger on 2011-07-04
HTML is *not *a *programming* language. Computer language, possibly.
'Nuff said.

---

### Post by 1clue on 2011-07-04
You guys need to stop using your personal definitions and start using the ones defined by the industry.  I can think of my iPhone as a jet fighter aircraft, and thus call myself a pilot with thousands of hours of experience, but that doesn't make it true.

Make me a PDF file that, when I execute it, it lets me design my house and helps me calculate wiring, plumbing, building materials necessary, heating, costs, etc.  Interactively.  Or one that plays chess.  Or one that handles my business accounts and applies cash from the bank statement to match to my invoices.  Make an XML file that plays music or lets me edit video, without any external files to help.  If it's a programming language then you should be able to statically link any libraries you need.

XML, when parsed by a standard parser, has some characteristics of a programming language when looked at from a certain perspective, and ONLY while it's being parsed.  That does not make it a programming language.  You could use an XML parser as a parser for a programming language, but that just means you have an obscenely cumbersome front end for a convoluted programming language that nobody would actually use.  The compiler/interpreter is somewhere else and is thus not XML.

A PDF is not in any way executable.  In order to be rendered, it needs additional software which translates the data in the document into a page which can be viewed or printed.  The rendering, the viewing and the printing are handled by something which is not in the document, and which is not inherently part of the computer hardware.  That makes those other things programs, and the PDF is data.

It's exactly the same with XML, HTML, and pretty much everything else we've talked about which are not considered programming languages by the industry.

---

### Post by Bandit on 2011-07-04
> **1clue said:**
> You guys need to stop using your personal definitions and start using the ones defined by the industry.  I can think of my iPhone as a jet fighter aircraft, and thus call myself a pilot with thousands of hours of experience, but that doesn't make it true.

Make me a PDF file that, when I execute it, it lets me design my house and helps me calculate wiring, plumbing, building materials necessary, heating, costs, etc.  Interactively.  Or one that plays chess.  Or one that handles my business accounts and applies cash from the bank statement to match to my invoices.  Make an XML file that plays music or lets me edit video, without any external files to help.  If it's a programming language then you should be able to statically link any libraries you need.

XML, when parsed by a standard parser, has some characteristics of a programming language when looked at from a certain perspective, and ONLY while it's being parsed.  That does not make it a programming language.  You could use an XML parser as a parser for a programming language, but that just means you have an obscenely cumbersome front end for a convoluted programming language that nobody would actually use.  The compiler/interpreter is somewhere else and is thus not XML.

A PDF is not in any way executable.  In order to be rendered, it needs additional software which translates the data in the document into a page which can be viewed or printed.  The rendering, the viewing and the printing are handled by something which is not in the document, and which is not inherently part of the computer hardware.  That makes those other things programs, and the PDF is data.

It's exactly the same with XML, HTML, and pretty much everything else we've talked about which are not considered programming languages by the industry.

This++

---

