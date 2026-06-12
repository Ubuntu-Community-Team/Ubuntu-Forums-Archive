---
title: "Web Page Programming"
date: 2010-09-28
forum: Server Platforms
---

### Post by PyrexKidd on 2010-09-28
I admin a heavy use FTP server that holds config files.

I has been necessary for me to develop several tools for maintaining those config files.  I have built the tools in Perl and every thing is great.  Except now it has become necessary for me to devolop a user interface for those tools. 

I am very proficient with Java and Perl, and familiar with VB .NET and C#/++.  None of the latter three have I ever heard of being used for web page programming.

What would be the most pain free way to develop a user interface?  I am new to web page programming and am looking for the `best` solution.  I've heard that Java embeds well in web pages, and a port from Perl to Java wouldn't be that difficult.  I've also heard that PHP (which looks syntactically very similar to Perl and Java) would be the `best` route to go.  While I am not totally against learning a new language, it might be more efficient for me to use one of the languages I am already familiar with.

Essentially I will need, one tool that will allow me to fill out several fields and click a button to generate config files (in the correct folder), one tool will need to be able to upload a CSV and then perform some processing on it, and a third tool will essentially be a web page based text editor.

Maybe I'm making things harder than they should be.  Any suggestions/thoughts/opinions/feeling/jokes/general commentaries would be appreciated.

Thanks in Advance.

---

### Post by windependence on 2010-09-28
I would pick php as it is syntactically similar to C++ and much lighter than java, plus it is widely used for web programming and also free and open unlike C# or <ugh> VB.
 
-Tim

---

### Post by SeijiSensei on 2010-09-28
I suggest you stick with perl and add the [mod_perl]("http://perl.apache.org/") module to Apache if it's not already present.

The advantage of using PHP is that there are lots of predefined functions for tasks like uploading files, database access, and the like, but I suspect there are a lot of similar items for Perl especially via CPAN.

---

