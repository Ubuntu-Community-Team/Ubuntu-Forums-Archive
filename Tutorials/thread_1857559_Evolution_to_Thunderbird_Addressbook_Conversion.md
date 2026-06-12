---
title: "Evolution to Thunderbird Addressbook Conversion"
date: 2011-10-10
forum: Tutorials
---

### Post by ds_shellback on 2011-10-10
[COLOR="Black"][SIZE="4"][CENTER]Migrating the evolution address book[/CENTER][/SIZE][/COLOR]

Using the online conversion utility listed in the Ubuntu help ducumentation here:-

[https://help.ubuntu.com/community/MigrateEvolutionToThunderbird]("https://help.ubuntu.com/community/MigrateEvolutionToThunderbird")

results in some of the evolution address book fields being lost eg. business address etc...

I've written the following AWK program (my first - so feel free to recommend improvements) to convert the .csv file generated from evolution into a format that will import into thunderbird. This is required because the .csv column order and content is different between the two programs.

Here's the AWK program (save to evototb.awk); evolution stores up to four email addresses per contact while thunderbird stores only two; I found this a bit of a draw back since several of my contacts have multiple email addresses.

```
BEGIN {
  FS="\",\"|\""
}
{
  gsub(/\\n/,",");
  print "\"" $2 "\",\"" \
  $3 "\",\"" \
  $2 " " $3 "\",\"" \
  $5 "\",\"" \
  $6 "\",\"" \
  $7 "\",\"\",\"" \
  $11 "\",\"" \
  $12 "\",\"" \
  $13 "\",\"" \
  $14 "\",\"" \
  $15 "\",\"" \
  $16 "\",\"" \
  $17 "\",\"" \
  $18 "\",\"" \
  $19 "\",\"" \
  $20 "\",\"" \
  $21 "\",\"" \
  $22 "\",\"" \
  $23 "\",\"" \
  $24 "\",\"" \
  $25 "\",\"" \
  $26 "\",\"" \
  $27 "\",\"" \
  $28 "\",\"" \
  $29 "\",\"" \
  $30 "\",\"" \
  $31 "\",\"" \
  $32 "\",\"" \
  $33 "\",\"" \
  $34 "\",\"" \
  $35 "\",\"\",\"\",\"\",\"\",\"" \
  $36 "\""
}

```

Export the evolution address book with the following command in a terminal; this results in an error which seems to be well known and can be ignored, the e-contacts.csv file is generated regardless. (NOTE: If You've got a different version of evolution you may need to adjust this command to suit the location - this was done on Ubuntu 11.04)

```
/usr/lib/evolution/2.32/evolution-addressbook-export --format=csv >e-contact.csv
```

Convert the .csv file using the above AWK program.

```
awk -f evototb.awk e-contacts.csv > tb-contacts.csv
```

You can then import the tb-contact.csv file from this into the thunderbird address book. 

Hope this helps

---

### Post by linux4me on 2011-10-26
Thank you so much! I just did a clean install of 11.10, knowing in advance I was going to have to switch to Thunderbird. I thought I was prepared, but the VCard import kept failing, and I couldn't find a solution for the error. I may have had something to do with some of the entries I had.

This did the trick.

Thanks for taking the time to post the solution and your AWK script.

---

