---
title: "Change Apache SSI Syntax?"
date: 2009-10-18
forum: Server Platforms
---

### Post by skrimpy on 2009-10-18
I've tried searching for this and can't find anything so it may not be possible, but it seems like it should be possible.

My SSI on my Apache server works just fine.  I'm a website owner and I build my own sites which are hosted on two different remote servers.  One server uses Apache and the same syntax for includes as is standard:
```

<!--#include file=""-->

```

The other server uses a different include syntax.  Because of this I have to develop two files for every page - one with the standard syntax as I build the page on my server, and one with the remote server's syntax when I upload it.

Is there any way for me tell Apache to recognize the other syntax, too?  I really do most of my work on the remote server with the non-standard syntax and I'd like to be able to eliminate building two copies of every page.  Switching from this server is not an option :)

Any help is greatly appreciated.

---

### Post by nsche on 2009-10-18
I think you would have to write your own Apache module to do that.  Not an impossible task but....  Can you get the other site to change over to Apache?

---

### Post by commandergc on 2009-10-18
is it just the start and end tags that are different? example
```

<!--#include file="somefile"  --> Or something like:
<%include file="somefile" %>

``` if that is the case then the tags can be change in the [apache config]("http://http://httpd.apache.org/docs/2.2/mod/mod_include.html").

Are the commands different? if so unfortunately you are stuck unless you write a module to do it.

---

### Post by Lars Noodén on 2009-10-19
@ skrimpy  : which httpd is running on the problem server, if it's not Apache?

---

### Post by skrimpy on 2009-10-20
@ Lars - I am pretty positive it is also an Apache server

@commandergc - it's not just a symbol change:

```
***include.shtml***
```

is the syntax.

@nsche - changing to another server isn't an option; I'm too pleased with the company to consider another, this is a minor annoyance but nothing I can't live with.

And it looks like live with it I shall, as I have no idea how to build Apache modules ;)

---

### Post by Lars Noodén on 2009-10-21
You can check to be sure.  Netcraft can be of help or you can query the server directly and see the identification string:

[INDENT][FONT="Courier New"]wget -S -O /dev/null [http://www.google.com/](http://www.google.com/)[/FONT][/INDENT]

If you develop your standard web pages in /var/www, you can have a staging area before uploading to the weird server.  e.g. /var/www-weird

After editing, you can sync the contents,

[INDENT][FONT="Courier New"]rsync -a /var/www/ /var/www-weird/[/FONT][/INDENT]

make sure they are valid XHTML

[INDENT][FONT="Courier New"]rsync -a /var/www/ /var/www-weird/[/FONT][/INDENT]

and then search and replace the pieces(*)


When you say the other server uses a different include syntax, what exactly is that syntax?








---

***** Here is a quick perl script to change includes

```

#!/usr/bin/perl

use strict;
use integer;
use warnings;
use less 'time';        # still unimplemented ;)

use HTML::TokeParser::Simple;

my $filename = shift
    or die( qq(Must provide a file to parse!\nUsage:  $0 filename\n));


my $parser = HTML::TokeParser::Simple->new($filename);

while ( my $token = $parser->get_token ) {

    unless ( $token->is_comment ) {
        print $token->as_is;

    } else {
        my $comment = $token->as_is;

        #
        ## Here is where the substitutions take place
        [B]$comment =~ s/-->/%>/
            if ( $comment =~ s/<!-- *include/<% foo-include/ );[/B]
        ##
        #

        print $comment;
    }
}

exit ( 0 );

```

---

### Post by skrimpy on 2009-10-21
this is the syntax:

```
***includes.shtml***
```

it's just using the Astrix trios rather than the comment structure used by the standard includes.  

I queried my website using wget and it did report it's an Apache server.  I'm not sure exactly how that server functions on the backend.  I've often joked with my husband (who is a database admin) that I wish he'd get a job with the company just so I could figure out how their backend works :p  But obviously they've got something changed so that the includes syntax needs to be ***includes.shtml***

Let me make sure I understand what you're suggesting:

I set up the staging area directory.  Then use rsync to transfer files from /var/www to the staging directory after I've made my changes and validated my xhtml.  Then I could run the perl script in the staging directory which would quickly change the includes statements to the non-standard syntax?

---

### Post by Lars Noodén on 2009-10-22
> **skrimpy said:**
> 
Let me make sure I understand what you're suggesting:

I set up the staging area directory.  Then use rsync to transfer files from /var/www to the staging directory after I've made my changes and validated my xhtml.  Then I could run the perl script in the staging directory which would quickly change the includes statements to the non-standard syntax?

Yes.  The reason for the staging area is so that if anything messes up in the transition, you still have the originals unharmed hopefully.  

The script can be modified to write out a copy, rename the original, then rename the copy.  Python and java work for xml parsing as well.  I just picked perl cause it's ubiquitous and, for me, convenient.

---

### Post by skrimpy on 2009-10-22
Lars, I tried setting up the staging area and running the script on a test file.  The script runs just fine and prints the output, but the includes syntax is not changing.  Any ideas on what I may be doing wrong?

---

### Post by Lars Noodén on 2009-10-25
> **skrimpy said:**
> Lars, I tried setting up the staging area and running the script on a test file.  The script runs just fine and prints the output, but the includes syntax is not changing.  Any ideas on what I may be doing wrong?

The script only sends to stdout.  It's up to you to have the steel nerves to try messing with the files on your file system.  One option is to add about four lines to the perl script to (safely) edit the file in place.  Another would be to write your own in python or java.

Yet another would be to treat the script like any other program and [redirect](http://linux.die.net/man/1/bash#Redirection) the output.  (See also [*The Advanced Bash-Scripting Guide*](http://linux.die.net/abs-guide/).  [Chapter 19. I/O Redirection](http://linux.die.net/abs-guide/io-redirection.html)) One way to do that would be with find:

```

find /var/www-weird/ -name '*.shtml' \
    -exec sh -c \
   '/usr/local/bin/foo.pl "{}" > "{}.tmp" && \
    mv "{}" "{}.orig" && \
    mv "{}.tmp" "{}"' \
    \;

```

Test these before running them and don't take anything you get from the net for gospel.  Here's what the above *should* do.  

The first line finds all files in the specified directory with the file name ending with shtml 

The second executes a shell just for the occasion.  

The third line passes the filename to the parsing script (assuming it is called /usr/local/bin/foo.pl) and runs it, redirecting the output into a file based on the original file name, but ending with '.tmp'

The fourth line changes the filename of the original by appending '.orig' to it.  

The fifth and final line takes away the .tmp ending from the new file.

---

