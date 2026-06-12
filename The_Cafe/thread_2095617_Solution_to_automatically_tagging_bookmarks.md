---
title: "Solution to automatically tagging bookmarks?"
date: 2012-12-17
forum: The Cafe
---

### Post by hwttdz on 2012-12-17
I'm looking for a means of automatically tagging my bookmarks since I previously used a folder system but there was a lot of overlap between categories. Something like delicious seems interesting, but that service seems to not allow one to import bookmarks, and additionally I would have to manually go through every bookmark and assign the tags...

Anyone have any interesting ideas, firefox addon, webservice, something else?

---

### Post by hwttdz on 2012-12-22
If you export as xbel this script will tag all your bookmarks, sadly I can't find any way to import xbel with tags... Feel free to offer improvements.  It currently relies on my own weird password convention.

```
#!/usr/bin/perl
use strict;
use warnings;
use List::MoreUtils qw(uniq);
use XML::Twig;
use XML::Twig::XPath;

my $file = shift;
my $twig = XML::Twig->new(index => ['bookmark']);
$twig->parsefile($file);

foreach my $node ($twig->findnodes('//bookmark'))
{
  my $href = $node->att('href');

  # skip over those nodes where the url does not begin with http
  if(!($href =~ m/^http/i)){next;}

  if(1 == $node->children_count('info'))
  {
    my $info = $node->last_child_matches('info');
    if(1 == $info->children_count('metadata'))
    {
      my $new_tags = &suggest_bookmarks($href);

      # if there are old tags
      if($info->last_child('metadata')->att_exists('tags'))
      {
        my $old_tags = $info->last_child('metadata')->att('tags');
        $new_tags = "$old_tags,$new_tags";
      }

      # tags should contain both old and new
      $node->last_child_matches('info')->last_child('metadata')->set_att(tags => "$new_tags");
    } # else # metadata != 1
  } # else # info != 1
}

$twig->print(pretty_print => 'indented');

$twig->purge;

sub suggest_bookmarks
{
  my @newtags = ();
  my $whoami = `whoami`;
  chomp($whoami);
  my $password = `make_password $whoami delicious`;
  chomp($password);
  my $sleep_delay = 1.5;

  my $twig = XML::Twig->new();

  # get tags for original domain
  my $url = shift;
  system("sleep $sleep_delay");
  my $suggested = `curl --silent https://$whoami:$password\@api.del.icio.us/v1/posts/suggest?url=$url`;
  chomp($suggested);
  if(defined($twig->safe_parse($suggested)))
  {
    foreach my $node ($twig->root->children('*[@tag]'))
    {
      push(@newtags, lc($node->att('tag')));
    }
    $twig->purge;
  }

  # then get tags for top level domain
  $url =~ s/(http:\/\/[^\/]*).*/$1/i;
  if(length($url) > 3) # make sure bookmark is not toplevel
  {
    system("sleep $sleep_delay");
    $suggested = `curl --silent https://$whoami:$password\@api.del.icio.us/v1/posts/suggest?url=$url`;
    chomp($suggested);
    if(defined($twig->safe_parse($suggested)))
    {
      foreach my $node ($twig->root->children('*[@tag]'))
      {
        push(@newtags, lc($node->att('tag')));
      }
      $twig->purge;
    }
  }

  @newtags = uniq(sort(@newtags));

  my $flattags = '';
  for my $tag (@newtags)
  {
    $flattags = "$flattags,$tag";
  }
  $flattags =~ s/^,//;
  return $flattags;
}

```

---

