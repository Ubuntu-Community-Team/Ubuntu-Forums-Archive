---
title: "Gcstar collection manager"
date: 2015-05-10
forum: The Cafe
---

### Post by ilpiero on 2015-05-10
Hi all,

I've been using GCstar collection manager for a while, to keep track of my huge disc collection.
Unfortunately the application is not maintained anymore and many plugins to fetch data from website went out of date.

I fixed the Discogs plugin, but it seems there is no way to contact the developers and the GCstar forum doen not allow to post.

What should I do with that code? How do I give it back to the community?




```
package GCPlugins::GCmusics::GCDiscogs;

###################################################
#
#  Copyright 2005-2010 Christian Jodar
#  Modified by Marco Venturini 2015  
#
#  This file is part of GCstar.
#
#  GCstar is free software; you can redistribute it and/or modify
#  it under the terms of the GNU General Public License as published by
#  the Free Software Foundation; either version 2 of the License, or
#  (at your option) any later version.
#
#  GCstar is distributed in the hope that it will be useful,
#  but WITHOUT ANY WARRANTY; without even the implied warranty of
#  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#  GNU General Public License for more details.
#
#  You should have received a copy of the GNU General Public License
#  along with GCstar; if not, write to the Free Software
#  Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA 02110-1301, USA
#
###################################################

use strict;
use utf8;
use JSON;

use GCPlugins::GCmusics::GCmusicsCommon;

{
    package GCPlugins::GCmusics::GCPluginDiscogs;

    use base 'GCPlugins::GCmusics::GCmusicsPluginsBase';
    use XML::Simple;
    use constant idString => "&token=UQcTbFJYjsLcxFkxWhvLLWTUZetVkFdYuQHXGeuV";
    use constant resultsPerPage => "30";

    sub parse
    {
        my ($self, $page) = @_;
        
        my $json        = JSON->new->utf8;
      	my $json_text   = $page;
        my $json_decoded = $json->decode( $json_text );
  		           
        
        #return if $page =~ /^<!DOCTYPE html/;
        my $xml;
        my $xs = XML::Simple->new;
        my $key = $self->{searchField};
        if ($self->{parsingList})
        {
            if ( $key eq 'artist' )
            {
              
               # #$xml = $xs->XMLin($page);               
               # my $artist = $xml -> {'artist'} -> {'name'};
               # my $release;
               # foreach $release ( keys( %{ $xml -> {'artist'} -> {'releases'} -> {'release'} } ) )
               # {
               #          $self->{itemIdx}++;
               #          my $title = $xml -> {'artist'} -> {'releases'} -> {'release'} -> {$release} -> {'title'};
               #          $self->{itemsList}[$self->{itemIdx}]->{url} = "https://api.discogs.com/releases/".$release;
               #          $self->{itemsList}[$self->{itemIdx}]->{title} = $title;
               #         # Enleve les blancs en debut de chaine
               #          $self->{itemsList}[$self->{itemIdx}]->{title} =~ s/^\s+//;
               #
               #      $self->{itemsList}[$self->{itemIdx}]->{artist} = $artist;
               #          # Enleve les blancs en fin de chaine
               #          $self->{itemsList}[$self->{itemIdx}]->{artist} =~ s/\s+$//;
               # }
                
               
            }
            elsif ( $key eq 'label' )
            {
                #$xml = $xs->XMLin($page);
                #my $release;
                #foreach $release ( keys( %{ $xml -> {'label'} -> {'releases'} -> {'release'} } ) )
                #{
                #         $self->{itemIdx}++;
                #         my $title = $xml -> {'label'} -> {'releases'} -> {'release'} -> {$release} -> {'title'};
                #         my $artist = $xml -> {'label'} -> {'releases'} -> {'release'} -> {$release} -> {'artist'};
                #         $self->{itemsList}[$self->{itemIdx}]->{url} = "https://api.discogs.com/releases/".$release;
                #         $self->{itemsList}[$self->{itemIdx}]->{title} = $title;
                #         # Enleve les blancs en debut de chaine
                #         $self->{itemsList}[$self->{itemIdx}]->{title} =~ s/^\s+//;
                #
                #         $self->{itemsList}[$self->{itemIdx}]->{artist} = $artist;
                #         # Enleve les blancs en fin de chaine
                #         $self->{itemsList}[$self->{itemIdx}]->{artist} =~ s/\s+$//;
                # }
            }
            else
            {
                #$xml = $xs->XMLin($page,
                #                  ForceArray => ['result', 'event'],
                #                  KeyAttr => {'release' => ''});
                my $release;
                 
                 
                #foreach $release ( @{ $xml->{'searchresults'}->{result} } )
                foreach $release ( @{$json_decoded->{results}})
                {
                    if ($release->{type} eq 'release')
                    {
                       $self->{itemIdx}++;
                       $self->{itemsList}[$self->{itemIdx}]->{url} = $release->{uri};                    
                       $self->{itemsList}[$self->{itemIdx}]->{release} = $release->{year};
                      
                       my $found = index($release->{title},"-");
                       if ( $found >= 0 )
                       {
                                       
                          $self->{itemsList}[$self->{itemIdx}]->{title} = substr($release->{title}, $found +length('-'),length($release->{title})- $found -length('-'));
                          # Enleve les blancs en debut de chaine
                          $self->{itemsList}[$self->{itemIdx}]->{title} =~ s/^\s+//;
                                            
                          $self->{itemsList}[$self->{itemIdx}]->{artist} = substr($release->{title}, 0, $found);
                          # Enleve les blancs en fin de chaine
                          $self->{itemsList}[$self->{itemIdx}]->{artist} =~ s/\s+$//;

                          # Clean up release summary
                          my $tmpTitle = $release->{title};
                          $tmpTitle =~ s/\- //;
                          
                          # Unsure about this line, seems to not be required anymore, and is breaking parsing
                          # of search results. EG - searching for "raw animals"
                          # $self->{itemsList}[$self->{itemIdx}]->{release} =~ s/^$tmpTitle //;
                       }
                       else
                       {
                          $self->{itemsList}[$self->{itemIdx}]->{title} = $release->{title};
                       }
                    }
                }
            }
        }
        else
        {
           # $xml = $xs->XMLin($page,
           #                   ForceArray => ['track', 'artist', 'image', 'label', 'genre', 'format'],
           #                   KeyAttr => {'track' => ''});
            $self->{curInfo}->{title} = $json_decoded->{title};
            $self->{curInfo}->{artist} = '';
            for my $art (@{$json_decoded->{artists}})
            {
                $self->{curInfo}->{artist} .= $art->{name}.', ';
            }     
            $self->{curInfo}->{artist} =~ s/, $//;
            $self->{curInfo}->{producer} = '';
            $self->{curInfo}->{composer} = '';
            for my $rel (@{$json_decoded->{extraartists}})
            {
                $self->{curInfo}->{producer} .= $rel->{name}.', '
                    if $rel->{role} eq 'Producer';
                $self->{curInfo}->{composer} .= $rel->{name}.', '
                    if (($rel->{role} eq 'Composed By') || ($rel->{role} eq 'Score') || ($rel->{role} eq 'Songwriter') || ($rel->{role} eq 'Written-By'));
            }
            $self->{curInfo}->{producer} =~ s/, $//;
            $self->{curInfo}->{composer} =~ s/, $//;
            $self->{curInfo}->{release} = $json_decoded->{released};
            for my $track(@{$json_decoded->{'tracklist'}})
            {
                my $duree = $track->{duration};
                $duree =~ /([0-9]+):([0-9]+)/;
                my $duree2 = int($1*60 + $2);
                my $position = "";
                # Sometimes the position is missing, which causes it to be an array
                if (!ref($track->{position}))
                {
                    $position = $track->{position};
                }
                $self->addTrack($track->{title}, $duree2, $position);
            }
            $self->{curInfo}->{tracks} = $self->getTracks;
            $self->{curInfo}->{running} = $self->getTotalTime;
            #for my $cover(@{$json_decoded->{images}->{image}})
            #{
            #    if ($self->{curInfo}->{cover} eq '')
            #    {
            #        if ($self->{bigPics})
            #        {
            #            $self->{curInfo}->{cover} = $cover->{uri};
            #        }
            #        else
            #        {
            #            $self->{curInfo}->{cover} = $cover->{uri};
            #            # Change to small res cover
            #            $self->{curInfo}->{cover} =~ s/image\/R-/image\/R-150-/;            
            #        }    
            #    }
            #   
            #}
            $self->{curInfo}->{label} = '';
            for my $label (@{$json_decoded->{labels}})
            {
                $self->{curInfo}->{label} .= $label->{name}.', ';
            }
            $self->{curInfo}->{label} =~ s/, $//;
            $self->{curInfo}->{genre} = '';
            for my $genre (@{$json_decoded->{genres}})
            {
                $self->{curInfo}->{genre} .= $genre.',';
            }
            $self->{curInfo}->{genre} =~ s/,$//;
            $self->{curInfo}->{origin} = $json_decoded->{country}; 
            $self->{curInfo}->{origin} =~ s/,$//;
            for my $format(@{$json_decoded->{formats}})
            {
                if (  $self->{curInfo}->{format} eq '')
                {
                    $self->{curInfo}->{format} = $format->{name};
                    $self->{curInfo}->{format} =~ s/,$//; 
                }
            }
            $self->{curInfo}->{web} = "https://api.discogs.com/releases/" . $json_decoded->{id};            
        }
    }

    sub new
    {
        my $proto = shift;
        my $class = ref($proto) || $proto;
        my $self  = $class->SUPER::new();
        bless ($self, $class);

        $self->{hasField} = {
            title => 1,
            artist => 1,
            release => 1
        };

        return $self;
    }

    sub preProcess
    {
        my ($self, $html) = @_;

        return $html;
    }
    
    sub decodeEntitiesWanted
    {
        return 0;
    }

    sub getSearchUrl
    {
        my ($self, $word) = @_;
        
        my $key = $self->{searchField};
        my $url;
        if ( $key eq 'title' )
        {
            #$url = "http://api.discogs.com/search?type=all&q=". $word ."&f=xml&api_key=e8f5ae8ba2";
            $url = "https://api.discogs.com/database/search?release_title=". $word ."&per_page=". resultsPerPage ."&page=1".idString;
        }
        elsif ( $key eq 'artist' )
        {
            #$url = "http://api.discogs.com/". $key ."/". $word ."?f=xml&api_key=e8f5ae8ba2"; 
            $url = "https://api.discogs.com/database/search?artist=". $word ."&per_page=". resultsPerPage ."&page=1".idString;
        }
        elsif ( $key eq 'label' )
        {
            #$url = "http://api.discogs.com/". $key ."/". $word ."?f=xml&api_key=e8f5ae8ba2"; 
            $url = "https://api.discogs.com/database/search?label=". $word ."&per_page=". resultsPerPage ."&page=1".idString;
        }
        
        return $url;
#        return "http://api.discogs.com/search?type=all&q=". $word ."&f=xml&api_key=e8f5ae8ba2";
    }
    
    sub getItemUrl
    {
        my ($self, $url) = @_;
        if (!$url)
        {
            # If we're not passed a url, return a hint so that gcstar knows what type
            # of addresses this plugin handles
            $url = "http://www.discogs.com";
        }
        else 
        {
            # Url isn't for the discogs api, so we need to find the release id
            # and return a url corresponding to the api page for this release  
       		my @urlParts = split /\//, $url;   
       		my $urlPartsLastIdx = @urlParts -1;  
   			$url = "https://api.discogs.com/releases/".$urlParts[$urlPartsLastIdx];
        }
       
        return $url;
    }

    sub changeUrl
    {
        my ($self, $url) = @_;
        
        return $self->getItemUrl($url);
    }

    sub getName
    {
        return 'Discogs';
    }
    
    sub getAuthor
    {
        return 'TPF';
    }
    
    sub getLang
    {
        return 'EN';
    }

    sub getCharset
    {
        my $self = shift;
    
        return "UTF-8";
    }
    
    sub getSearchCharset
    {
        my $self = shift;

        # Need urls to be double character encoded
        return "utf8";
    }

    sub convertCharset
    {
        my ($self, $value) = @_;
        return $value;
    }

    sub getNotConverted
    {
        my $self = shift;
        return [];
    }

    sub getSearchFieldsArray
    {
        return ['title', 'artist', 'label'];
    }
}

1;

```

---

### Post by mainmeister on 2015-05-10
Post to github

---

### Post by ilpiero on 2015-05-15
there seem that no repository exists there (nor under sourceforge) for gcstart... correct?

---

### Post by slickymaster on 2015-05-15
> **ilpiero said:**
> Hi all,

I've been using GCstar collection manager for a while, to keep track of my huge disc collection.
Unfortunately the application is not maintained anymore and many plugins to fetch data from website went out of date.

I fixed the Discogs plugin, but it seems there is no way to contact the developers and the GCstar forum doen not allow to post.

What should I do with that code? How do I give it back to the community?
<---snip--->
Here you go: [http://www.gcstar.org/contribute.en.php](http://www.gcstar.org/contribute.en.php)

---

### Post by ilpiero on 2015-05-20
The website is online but unmantained, do you have any contact with the developers or you just googled?

---

### Post by slickymaster on 2015-05-21
> **ilpiero said:**
> The website is online but unmantained, do you have any contact with the developers or you just googled?
Sorry, no contacts at all, I simply googled it.

---

