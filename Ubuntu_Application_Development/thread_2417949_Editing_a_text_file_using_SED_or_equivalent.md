---
title: "Editing a text file using SED or equivalent"
date: 2019-04-29
forum: Ubuntu Application Development
---

### Post by Lewis Arthurton on 2019-04-29
Hello Ubuntu Folks 

I am looking to edit a text file using sed or whatever method works to make the following changes:

Original: 
```
Chromosome      ena     CDS     153     1535    .       +       0       transcript_name "transcript:AAS13770";  gene_id "gene:WD_0001"; gene_name "dnaA";
Chromosome      ena     exon    3028    3115    .       +       .       transcript_name "transcript:WD_tRNA-Leu-1-1"; gene_id "gene:WD_tRNA-Leu-1"; gene_name "WD_tRNA-Leu-1"; 
```

New: 
```
Chromosome      ena     CDS     153     1535    .       +       0       **transcript_id "transcript:AAS13770";** transcript_name "transcript:AAS13770"; gene_id "gene:WD_0001"; gene_name "dnaA";
Chromosome      ena     exon    3028    3115    .       +       .       **transcript id transcript:WD_tRNA-Leu-1-1"; **transcript_name "transcript:WD_tRNA-Leu-1-1"; gene_id "gene:WD_tRNA-Leu-1"; gene_name "WD_tRNA-Leu-1"; 
```

Essentially I would like to take the transcript_name ("transcript:AAS13770"), add a new field before with transcript_id and paste the transcript name after this ending with a semi colon and continue this for every line. 

Does anyone have any idea how to do this? I'm looking at sed but I cannot get my head around it. sorry to be a pain.

Best wishes,

Lewis

---

### Post by TheFu on 2019-04-29
The parts of the line that are identical don't really matter. It is the parts that need to be different and some method of locating where that difference can be 100% assured in each line.

sed works on 1 line at time.  So does awk, which is a little more powerful.

```
sed -e 's/transcript_name/transcript_id/g' inputfile > output 
``` is how you replace things.  If you want to insert things, the you can match on the leading whitespace and transcript - something like this: 
```
sed -e 's/transcript_name/transcript_id "transcript:AAS13770"; transcript_name/g' inputfile > output
```

So perform other changes when the pattern isn't 100%, you can either run another sed command and pass the output from the first into the second (via pipes) or add another **-e s///g** stanza or use tools that work on column locations or have better grouping capabilities like ruby, python or perl.

For amazing text processing, using another scripting language like perl would be my choice.  Perl has a chunking function that will split on any delimiter you like (whitespace is default) and easily store each line into an array.
```
#!/usr/bin/env perl
 
while (<>){
   chomp;
   my @line = split(/ +/, $_);
   print join ' ', @line, "\n";
   $line[8] = $line[8] . "-foo";
   print "8: ", $line[8], "\n";
}

```

The @line is an array, so $line[8] should have the 'transcript_name' inside. If you modify just that part of the array before printing it out, you can make it say anything you like.  See above.  There are 50 other ways to handle this too. Arrays and splitting is 1, probably not even the best.  If all you care about is the output line, then I wouldn't bother assigning anything inside the array. Let the 'print' handle what you need.

Run this with **filename.pl inputfile**.  Output goes to stdout so it can be used as a filter.  If you use the output from another program's stdout as stdin to the perl or sed, then is looks like this:
```
cat file | filename.pl | sed -e "s/whatever/something new/g" |more
```
Filters that use stdin and write to stdout are very powerful.  sed, grep, cut, join and 150 other Unix tools work that way.

```
du -h * | sort -hr |more
```
That's for lurkers.

---

### Post by lensman3 on 2019-07-06
Use "ed".  "ed" predates vi, but vi still has the "ed" commands.

Load the interactive version of ed by "ed <filename".  To print the file to the screen enter "1,$p" at the prompt.

Try the command 'g/^/m0'   .   Do not save as this command reverses ALL the lines in the file.  (Works in vim too).

The only place I have seen a manual is Appendix 1 of 'The UNIX programming Environment' by Kernighan and Pike (1984).

---

