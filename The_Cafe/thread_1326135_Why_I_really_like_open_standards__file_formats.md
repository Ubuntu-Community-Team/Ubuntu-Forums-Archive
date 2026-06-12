---
title: "Why I really like open standards / file formats"
date: 2009-11-14
forum: The Cafe
---

### Post by FunkyRes on 2009-11-14
Working on my biological related hobby web site, I'm generating hexagon locality maps for reptile and amphibian species in my county.

For data source, I'm using a combination of my own records and vertebrate museum records.

Getting the Cal Berkeley MVZ records in was fairly easy, they provide an option to download the datasets in XML so I could easily extract the info I needed and insert into my database.

The other major source of data was California Academy of Sciences.
They only provide dataset as a text file. I found it extremely difficult to parse the data with awk, but interestingly, gnumeric had no problem opening it and sorting the data appropriately into columns and rows.

That's where the beauty of open standards really shined.

saved file as gnumeric format, gunzip it, and I have an xml file I could then parse with libxml2 based tools (DOMDocument class in php to be specific) and get the data I needed all sorted out and into my database.

```

<?php
set_time_limit(3000); // it's a large file
$source = '/srv/shastaherps/input.xml';

function getNodeTextChild($dom,$node) {
   // for a node that can only have one text child, this returns the child.
   //  otherwise it returns ''
   $return='';
   if ($node->hasChildNodes()) {
      $n = $node->childNodes->length;
      if ($n == 1) {
         $children=$node->childNodes;
         foreach ($children as $child) {
            if ($child->nodeType == XML_TEXT_NODE) {
               $return = $child->nodeValue;
               }
            }
         }
      }
   return $return;
   }

$pre = new DOMDocument('1.0','UTF-8');
$mus = new DOMDocument('1.0','UTF-8');
$wrap = $mus->createElement('wrap');
if (file_exists($source)) {
   $buffer = file_get_contents($source);
   $buffer = preg_replace('/gnm:/','',$buffer);
   $buffer = preg_replace('/office:/','',$buffer);
   //header('Content-type: text/plain');
   //die($buffer);
   $pre->loadXML($buffer);
   
   //header('Content-type: text/plain');
   //print $pre->saveXML();
   //die();   
   
   $n=0;
   $intrst = $pre->getElementsByTagName('Cell');
   for ($i=0;$i<$intrst->length;$i++) {
//   for ($i=0;$i<500;$i++) {
      $myitem = $intrst->item($i);
      $t = $myitem->getAttribute('Row');
      if ($t > $n) {
         //we are at a new record
         if (isset($record)) {
            $wrap->appendChild($record);
            }
         $record = $mus->createElement('record');
         $n = (0 + $t);
         }
      $col = 0 + $myitem->getAttribute('Col');
      if ($n > 0) {
         switch ($col) {
            case 1 :
               $newval = getNodeTextChild($pre,$myitem);
               $newnode = $mus->createElement('cat',$newval);
               $record->appendChild($newnode);
               break;
            case 4 :
               $newval = getNodeTextChild($pre,$myitem);
               $newnode = $mus->createElement('mus',$newval);
               $record->appendChild($newnode);
               break;
            case 30 :
               $newval = getNodeTextChild($pre,$myitem);
               $newnode = $mus->createElement('locale',$newval);
               $record->appendChild($newnode);
               break;
            case 32 :
               $newval = getNodeTextChild($pre,$myitem);
               $newnode = $mus->createElement('year',$newval);
               $record->appendChild($newnode);
               break;
            case 44 :
               $newval = getNodeTextChild($pre,$myitem);
               $newnode = $mus->createElement('day',$newval);
               $record->appendChild($newnode);
               break;
            case 45 :
               $newval = getNodeTextChild($pre,$myitem);
               $newnode = $mus->createElement('month',$newval);
               $record->appendChild($newnode);
               break;
            case 54 :
               $newval = getNodeTextChild($pre,$myitem);
               $newnode = $mus->createElement('lat',$newval);
               $record->appendChild($newnode);
               break;
            case 55 :
               $newval = getNodeTextChild($pre,$myitem);
               $newnode = $mus->createElement('lon',$newval);
               $record->appendChild($newnode);
               break;  
            case 58 :
               $newval = getNodeTextChild($pre,$myitem);
               $newnode = $mus->createElement('taxon',$newval);
               $record->appendChild($newnode);
               break;
            } //end switch
         } // end if n > 0
      } // end i loop
   $wrap->appendChild($record);
   $mus->appendChild($wrap);

   $mus->preserveWhiteSpace = false;
   $mus->formatOutput   = true;
   header('Content-type: text/plain');
   print $mus->saveXML();
   }

```

That made a nice xml file for me that was then easy to parse with my general import utility (which does things like update old taxonomy, makes sure the georeference is actually in my county, and then makes a gpx file so I can run it through [http://www.gpsvisualizer.com/elevation](http://www.gpsvisualizer.com/elevation) and get very accurate elevations)

Took a long time to execute because the loop was huge (bunch of data I have no use for) but open file formats made it possible.

---

