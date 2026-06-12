---
title: "Wiki faq conversion -- need perl help"
date: 2005-04-09
forum: The Cafe
---

### Post by jnoreiko on 2005-04-09
The comments in the Wiki FAQ page ( [http://www.ubuntulinux.org/wiki/FrequentlyAskedQuestions](http://www.ubuntulinux.org/wiki/FrequentlyAskedQuestions) ) say it needs to be converted to moin format.

So... I made a perl script that in theory would do this.

It works, except the output is all wrong ;)  -- seriously though, reading the markup from a local file works, and it creates a data structure which can then be run through and printed off into moin format. But really weird things are happening to the output. I suspect this is a to do with me being on windows and the source from the wiki having unix line endings.

Could someone who's better at perl than I am take a look please?

```

#!/usr/bin/perl

# convert ubuntu wiki faq to moin
use warnings;
use File::Slurp;

#$\ = "\n";
$n  = "\n";

#############################################

$text = read_file( 'wikifaq.txt' );
open OUTPUT, '>wikifaqmoin.txt';

#############################################


@items = $text =~ m[^\.\. \|(\w+)\|.*replace::\s*(.*)$]mg;


while (@items) {
  my $code      = shift @items;
  my $question  = shift @items;
  (my $answer)  = $text =~ m[\|$code\|\s*\n-+\s*\n(.*?)\s*^\|]ms; 
  
  $faqs{$code} = {
    question  => $question,
    answer    => $answer,
  }
  
}


($toc) = $text =~ m[^Questions...\s*^-+\s*\n(.*?)^-]ms;

for (split "\n", $toc) {
  /^\* \*\*(.*)\*\*/ and do {
    # heading
    print OUTPUT "== $1 ==\n";
  };
  /^  - \|(.*)\|_/ and do {
    # question
    print OUTPUT '===', $faqs{$1}->{question}, '===';
    print OUTPUT $faqs{$1}->{answer};
  };


}



```

---

### Post by jnoreiko on 2005-04-09
Getting the same errors on ubuntu.

Turns out my text document was somehow full of control characters...  :-s 

Fixing it now...

---

