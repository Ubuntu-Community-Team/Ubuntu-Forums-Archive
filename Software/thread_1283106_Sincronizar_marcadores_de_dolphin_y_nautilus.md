---
title: "Sincronizar marcadores de dolphin y nautilus"
date: 2009-10-05
forum: Software
---

### Post by electronpositivo on 2009-10-05
Buenas!

Me gustaría saber si es posible realizar una sincronización automática entre el fichero /home/user/.gtk-bookmarks y el fichero /home/user/.local/share/user-places.xbel que según tengo entendido almacenan los marcadores de nautilus y dolphin respectivamente.

¿Alguien tiene idea?

---

### Post by ermeyers on 2009-10-05
English translation: [http://babelfish.yahoo.com](http://babelfish.yahoo.com)
To synchronize markers of dolphin and nautilus Good! I would like to know if it is possible to realise an automatic synchronization between the /home/user/.gtk-bookmarks file and the /home/user/.local/share/user-places.xbel file that according to I have understood respectively stores to the markers of nautilus and dolphin. Somebody has idea?

Write a program that does the synchronization, named $HOME/bin/sync_markers.sh .

Load the program call into your crontab.  "man crontab" and "man 5 crontab" for info.

$crontab -e
# m h  dom mon dow   command
*/5 * * * * $HOME/bin/sync_markers.sh

---

### Post by guillermolisi on 2009-10-05
> **ermeyers said:**
> English translation: [http://babelfish.yahoo.com](http://babelfish.yahoo.com)
To synchronize markers of dolphin and nautilus Good! I would like to know if it is possible to realise an automatic synchronization between the /home/user/.gtk-bookmarks file and the /home/user/.local/share/user-places.xbel file that according to I have understood respectively stores to the markers of nautilus and dolphin. Somebody has idea?

Write a program that does the synchronization, named $HOME/bin/sync_markers.sh .

Load the program call into your crontab.  "man crontab" and "man 5 crontab" for info.

$crontab -e
# m h  dom mon dow   command
0-59/5 * * * * $HOME/bin/sync_markers.sh
Thank you for you literal translation again.

Please, Could you post that program to complete your idea ? (Por favor, podrias mostrar ese programa para completar tu idea ?)

---

### Post by ermeyers on 2009-10-05
> Please, Could you post that program to complete your idea ?

English:
I don't use dolphin or nautilus, so I don't know their file format in "~/.local/share/user-places.xbel".  I do have "~/.gtk-bookmarks", and that's a very easy text format.  Post short example of the file format for "~/.local/share/user-places.xbel", and I might humor you.

Spanish:
I don' delfín o nautilus del uso de t, tan yo don' t sabe su formato de archivo en " ~/.local/share/user-places.xbel". Tengo " ~/.gtk-bookmarks" , y that' formato de texto muy fácil del S.A. Fije el ejemplo corto del formato de archivo para el " ~/.local/share/user-places.xbel" , y puede ser que humor le. --Eric

---

### Post by guillermolisi on 2009-10-05
> **ermeyers said:**
> English:
I don't use dolphin or nautilus, so I don't know their file format in "~/.local/share/user-places.xbel".  I do have "~/.gtk-bookmarks", and that's a very easy text format.  Post short example of the file format for "~/.local/share/user-places.xbel", and I might humor you.

Spanish:
I don' delfín o nautilus del uso de t, tan yo don' t sabe su formato de archivo en " ~/.local/share/user-places.xbel". Tengo " ~/.gtk-bookmarks" , y that' formato de texto muy fácil del S.A. Fije el ejemplo corto del formato de archivo para el " ~/.local/share/user-places.xbel" , y puede ser que humor le. --Eric
Eric dice que se le muestre un pequeño ejemplo del formato del archivo "~/.local/share/user-places.xbel" y podria alegrarnos con alguna posible solucion.

BTW, Eric, Babelfish works much better making translations to English than to Spanish :D

---

### Post by ermeyers on 2009-10-05
> BTW, Eric, Babelfish works much better making translations to English than to Spanish

You get what I get from it.;)

English translation from [http://translation.paralink.com](http://translation.paralink.com) :
Eric says that one shows him a small example of the format of the file " ~/.local/share/user-places.xbel " and it might make us happy with some possible solution.

---

### Post by electronpositivo on 2009-10-06
> **ermeyers said:**
> English:
Eric says that one shows him a small example of the format of the file " ~/.local/share/user-places.xbel " and it might make us happy with some possible solution.

OK. My  "~/.local/share/user-places.xbel" is:
```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE xbel>
<xbel xmlns:bookmark="http://www.freedesktop.org/standards/desktop-bookmarks" xmlns:mime="http://www.freedesktop.org/standards/shared-mime-info" xmlns:kdepriv="http://www.kde.org/kdepriv" >
 <bookmark href="file:///home/sergio/.local/share" >
  <title>Share</title>
  <info>
   <metadata owner="http://freedesktop.org" >
    <bookmark:icon name="inode-directory" />
   </metadata>
   <metadata owner="http://www.kde.org" >
    <ID>1254734977/2</ID>
   </metadata>
  </info>
 </bookmark>
</xbel>
```

And the same bookmark in nautilus file "~/.gtk-bookmarks" is:
```
file:///home/users/profesores/sergio/.local/share Share

```

---

### Post by ermeyers on 2009-10-06
Why is it "/home/sergio" in one and "/home/users/profesores/sergio" in the other?
  [   ]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=8060451")
[	 		]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=8060451")

---

### Post by ermeyers on 2009-10-06
Install Perl module:
```

sudo cpan XML::Element

```Example **read_text_markers.pl**:
(need to find the logic for ID's like "1254734977/2")
```

#!/usr/bin/perl -w                                                                    
##                                                                                    

use strict;

use warnings;

require XML::Element;

my $xml_tree = XML::Element->new( '~pi', text => 'xml version="1.0" encoding="UTF-8"' );

my $doctype = XML::Element->new( '~declaration', text => 'DOCTYPE xbel' );

$xml_tree->push_content( $doctype );

my $xbel = XML::Element->new( 'xbel', 'xmlns' => 'http://www.freedesktop.org/standards/desktop-bookmarks',
                                      'xmlns:mime' => 'http://www.freedesktop.org/standards/shared-mime-info',
                                      'xmlns:kdepriv' => 'http://www.kde.org/kdepriv',
                             );


open( FH, "$ENV{'HOME'}/.gtk-bookmarks" ) || die( "opening ~/.gtk-bookmarks: $!\n" );

while( <FH> )
{
   chop();

   next if ( m/^\s*$/ );

   my ( $bm_uri, $bm_label ) = m/^([^ ]+)[  ]?([^ ]*)$/;

   my $bookmark = XML::Element->new( 'bookmark', 'href' => $bm_uri );

   my $title = XML::Element->new( 'title' );

   $title->push_content( $bm_label );

   $bookmark->push_content( $title );

   my $info = XML::Element->new( 'info' );

   my $metadata1 = XML::Element->new( 'metadata', 'owner' => 'http://freedesktop.org' );

   my $bookmark_icon = XML::Element->new( 'bookmark:icon', 'name' => 'inode-directory' );

   $metadata1->push_content( $bookmark_icon );

   $info->push_content( $metadata1 );

   my $metadata2 = XML::Element->new( 'metadata', 'owner' => 'http://www.kde.org' );

   my $id = XML::Element->new( 'ID' );

   $id->push_content( '1254734977/2' );

   $metadata2->push_content( $id );

   $info->push_content( $metadata2 );

   $bookmark->push_content( $info );

   $xbel->push_content( $bookmark );

} ## end while

close( FH );

$xml_tree->push_content( $xbel );

print $xml_tree->as_XML() . "\n";

$xml_tree->delete();

```
Example **read_xml_markers.pl**:
```

#!/usr/bin/perl -w
##

use strict;

use warnings;

require XML::TreeBuilder;

my $xml_tree = XML::TreeBuilder->new();

$xml_tree->parse_file( "$ENV{'HOME'}/.local/share/user-places.xbel" );

foreach my $xml_entry ( $xml_tree->find_by_tag_name( 'bookmark' ) )
{
   my $title = $xml_entry->find_by_tag_name( 'title' );

   my $label = $title->content()->[0];

   my $uri = $xml_entry->attr( 'href' );

   print "$uri $label\n";

} ## end foreach

$xml_tree->delete();

```

---

### Post by guillermolisi on 2009-10-06
Eric

Do you know the package name for Ubuntu that include/contains XML::Element module ?
The idea behind the question is to use the Ubuntu repositories instead Cpan servers.

Traduccion
Conoces el nombre del paquete para Ubuntu que incluye/contiene al modulo XML::Element ?
La idea es instalarlo desde los repositorios Ubuntu en lugar de usar servidores Cpan.

Thank you !

---

### Post by ermeyers on 2009-10-06
I don't see it.  I found libhtml-tree-perl with HTML::Element, but no libxml-tree-perl with XML::Element.  I still use CPAN for Perl, because not everything gets packaged. --Eric

---

### Post by guillermolisi on 2009-10-06
> **ermeyers said:**
> I don't see it.  I found libhtml-tree-perl with HTML::Element, but no libxml-tree-perl with XML::Element.  I still use CPAN for Perl, because not everything gets packaged. --Eric
Traduccion
No lo veo. Encontre libhtml-tree-perl con HTML::Element pero no encontre libxml-tree-perl con XML::Element. Utilizo CPAN para Perl porque no todo resulta empaquetado.

---

### Post by electronpositivo on 2009-10-06
> **ermeyers said:**
> Why is it "/home/sergio" in one and "/home/users/profesores/sergio" in the other?
  [   ]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=8060451")
[	 		]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=8060451")

It's a mistake. It's /home/sergio in both.

Traducción: Es un error. Es /home/sergio en ambos.

---

### Post by electronpositivo on 2009-10-07
ermeyers, works perfectly!

But I have observed that a small error occurs in case the nautilus bookmark has the same name as the final directory. For example, if I add a bookmark named "Documents" which refers to "/home/ users/ Documents", in file ~/.gtk-bookmarks "does not appear the word "Documents" after the path "/home/users/Documents":

```

file:/home/users/sergio/.local/share Share
file:/home/sergio/Documents

```

This marker produces an inconsistency in the generated XML when <title> tag.

What would be the modification to perform on "read_text_markers.pl? : confused:

Thanks for your scripts so good!

traducción:
[I]ermeyers, ¡funciona perfectamente! 

Pero he observado que se produce un pequeño error en caso que el marcador en nautilus tenga el mismo nombre que el directorio final. Por ejemplo, si añado un marcador llamado "Documentos" que hace referencia a "/home/users/Documentos", en el fichero "~/.gtk-bookmarks" no aparece la palabra "Documentos" después de la ruta "/home/users/Documentos":

```

file:///home/users/profesores/sergio/.local/share Share
file:///home/sergio/Documentos

```

Este marcador produce una inconsistencia en el XML cuando genera la etiqueta <title>.

¿Cuál sería la modificación a realizar en "read_text_markers.pl"? :confused:

!Gracias por tus scripts tan buenos![/I]

---

### Post by guillermolisi on 2009-10-07
Thank you so much Eric ! We appreciate your help !

Trad: Muchisimas gracias Eric ! Valoramos tu ayuda !

---

### Post by ermeyers on 2009-10-07
At top of file add "require File::Basename;":
```

require XML::Element;

require File::Basename;


```

In while loop add IF statement:
```

   my ( $bm_uri, $bm_label ) = m/^([^ ]+)[  ]?([^ ]*)$/;

   if ( $bm_label eq '' )
   {
      $bm_label = File::Basename::basename( $bm_uri );

   } ## end if


```

---

### Post by electronpositivo on 2009-12-14
Thank you very much ermeyers!

---

