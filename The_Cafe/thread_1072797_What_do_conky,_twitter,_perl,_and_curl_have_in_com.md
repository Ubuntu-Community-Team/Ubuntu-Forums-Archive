---
title: "What do conky, twitter, perl, and curl have in common?"
date: 2009-02-17
forum: The Cafe
---

### Post by bosp7 on 2009-02-17
This script:

```

#!/usr/bin/perl

use XML::Simple;
use Data::Dumper;
use Text::Wrap;
use Time::Piece;

$xml = new XML::Simple (KeyAttr=>[]);

# change userid:passwd to your twitter account info
system('curl -s -u "userid:passwd" http://twitter.com/statuses/friends_timeline.xml -o /tmp/twitdata.xml');
$data = $xml->XMLin("/tmp/twitdata.xml");

binmode STDOUT, ":utf8";

$Text::Wrap::columns = 60;

foreach $e (@{$data->{status}})
{
        $user = '${font Sans:style=Bold:size=7}${color darkred}' . $e->{user}->{screen_name} . ':${color}${font Sans:size=7} ';
        $time = Time::Piece->strptime($e->{created_at}, "%a %b %d %H:%M:%S %z %Y");
        $time += $time->localtime->tzoffset;
        $status = $e->{text};
        print $user;
        print '${font Sans:size=6}(' . $time->strftime("%a %I:%M:%S %P") . ')${font}' . "\n";
        print wrap('', '', $status);
        print "\n\n";
}

```

and here's my .conkyrc file to display it:

```

background yes
font Sans:size=7
xftfont Sans:size=7
use_xft yes
xftalpha 0.1
update_interval 60
total_run_times 0
own_window no
#own_window_type override
#own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
minimum_size 150 5
maximum_width 800
default_color ffffff
default_shade_color 000000
default_outline_color 000000
alignment top_left
gap_x 5
gap_y 40
no_buffers yes
text_buffer_size 4096
#cpu_avg_samples 2
override_utf8_locale no
uppercase no # set to yes if you want all text to be in uppercase
use_spacer no

TEXT

${font Sans:size=7}${execp get-twit}

```

---

