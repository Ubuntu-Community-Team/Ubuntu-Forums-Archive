---
title: "DVD Jon hacks Media Player file encryption"
date: 2005-09-02
forum: The Cafe
---

### Post by newbie2 on 2005-09-02
"Norway's best known IT export, DVD Jon, has hacked encryption coding in Microsoft's Windows Media Player, opening up content broadcast for the multimedia player to alternative devices on multiple platforms.

Jon Lech Johansen has reverse engineered a proprietary algorithm, which is used to wrap Media Player NSC files and ostensibly protect them from hackers sniffing for the media's source IP address, port or stream format. He has also made a decoder available."
[http://www.theregister.co.uk/2005/09/02/dvd_jon_mediaplayer/](http://www.theregister.co.uk/2005/09/02/dvd_jon_mediaplayer/)

/*****************************************************************************
 * nscdec.c: NSC decoder 1.0
 *****************************************************************************
 * Copyright (C) 2005 Jon Lech Johansen <jon@nanocrew.net>
 *
 * This program is free software; you can redistribute it and/or modify
 * it under the terms of the GNU General Public License as published by
 * the Free Software Foundation; either version 2 of the License, or
 * (at your option) any later version.
 *
 * This program is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 * GNU General Public License for more details.
 *
 * You should have received a copy of the GNU General Public License
 * along with this program; if not, write to the Free Software
 * Foundation, Inc., 59 Temple Place - Suite 330, Boston, MA  02111, USA.
 *****************************************************************************/

#include <stdio.h>
#include <ctype.h>
#include <iconv.h>
#include <string.h>
#include <stdlib.h>

static const unsigned char inverse[ 128 ] =
{
    0xFF, 0xFF, 0xFF, 0xFF, 0xFF, 0xFF, 0xFF, 0xFF, 0xFF, 0xFF, 0xFF, 0xFF,
    0xFF, 0xFF, 0xFF, 0xFF, 0xFF, 0xFF, 0xFF, 0xFF, 0xFF, 0xFF, 0xFF, 0xFF,
    0xFF, 0xFF, 0xFF, 0xFF, 0xFF, 0xFF, 0xFF, 0xFF, 0xFF, 0xFF, 0xFF, 0xFF,
    0xFF, 0xFF, 0xFF, 0xFF, 0xFF, 0xFF, 0xFF, 0xFF, 0xFF, 0xFF, 0xFF, 0xFF,
    0x00, 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0xFF, 0xFF,
    0xFF, 0xFF, 0xFF, 0xFF, 0xFF, 0x0A, 0x0B, 0x0C, 0x0D, 0x0E, 0x0F, 0x10,
    0x11, 0x12, 0x13, 0x14, 0x15, 0x16, 0x17, 0x18, 0x19, 0x1A, 0x1B, 0x1C,
    0x1D, 0x1E, 0x1F, 0x20, 0x21, 0x22, 0x23, 0xFF, 0xFF, 0xFF, 0xFF, 0xFF,
    0xFF, 0x24, 0x25, 0x26, 0x27, 0x28, 0x29, 0x2A, 0x2B, 0x2C, 0x2D, 0x2E,
    0x2F, 0x30, 0x31, 0x32, 0x33, 0x34, 0x35, 0x36, 0x37, 0x38, 0x39, 0x3A,
    0x3B, 0x3C, 0x3D, 0x3E, 0xFF, 0x3F, 0xFF, 0xFF
};

static int load_byte( unsigned char encoding_type,
                      unsigned char *output, char **input,
                      unsigned char *j, unsigned char *k )
{
    *output = 0;

    if( encoding_type == 1 )
    {
        if( isxdigit( **input ) == 0 )
            return -1;

        if( isdigit( **input ) == 0 )
            *output = (toupper( **input ) - 7) * 16;
        else
            *output = **input * 16;

        (*input)++;

        if( isxdigit( **input ) == 0 )
            return -1;

        if( isdigit( **input ) == 0 )
            *output |= toupper( **input ) - 0x37;
        else
            *output |= **input - 0x30;

        (*input)++;
    }
    else if( encoding_type == 2 )
    {
        unsigned char **uinput = (unsigned char **)input;

        if( **uinput > 127 || inverse[ **uinput ] == 0xFF )
            return -1;

        if( *k == 0 )
        {
            if( (*uinput)[ 1 ] > 127 || inverse[ (*uinput)[ 1 ] ] == 0xFF )
                return -1;

            *output = (inverse[ (*uinput)[ 0 ] ] * 4) |
                        (inverse[ (*uinput)[ 1 ] ] / 16);

            *j = inverse[ (*uinput)[ 1 ] ] * 16;
            *k = 4;

            (*uinput) += 2;
        }
        else if( *k == 2 )
        {
            *output = *j | inverse[ **uinput ];

            *j = 0;
            *k = 0;

            (*uinput)++;
        }
        else if( *k == 4 )
        {
            *output = (inverse[ **uinput ] / 4) | *j;

            *j = inverse[ **uinput ] * 64;
            *k = 2;

            (*uinput)++;
        }
    }

    return 0;
}

int main( int argc, char **argv )
{
    int ret = 0;

    unsigned int i;
    unsigned char tmp;
    unsigned char j, k;
    unsigned int length;
    unsigned char encoding_type;
    unsigned char *buffer;

    if( argc != 2 )
    {
        fprintf( stderr, "Usage: nscdec string\n" );
        return 1;
    }

    char *p_input = &argv[ 1 ][ 0 ];

    if( strlen( p_input ) < 15 )
    {
        fprintf( stderr, "Input string less than 15 characters\n" );
        return 1;
    }

    if( load_byte( 1, &encoding_type, &p_input, NULL, NULL ) )
    {
        fprintf( stderr, "Unable to get encoding type\n" );
        return 1;
    }

    if( encoding_type != 1 && encoding_type != 2 )
    {
        fprintf( stderr, "Encoding type %d is not supported\n",
                 encoding_type );
        return 1;
    }

    printf( "Encoding type: %d\n", encoding_type );

    j = k = 0;

    if( load_byte( encoding_type, &tmp, &p_input, &j, &k ) )
    {
        fprintf( stderr, "load_byte failed\n" );
        return 1;
    }

    for( i = 0; i < 4; i++ )
    {
        if( load_byte( encoding_type, &tmp, &p_input, &j, &k ) )
        {
            fprintf( stderr, "load_byte failed\n" );
            return 1;
        }
    }

    length = 0;
    for( i = 4; i; i-- )
    {
        if( load_byte( encoding_type, &tmp, &p_input, &j, &k ) )
        {
            fprintf( stderr, "load_byte failed\n" );
            return 1;
        }
        length |= tmp << ((i - 1) * 8);
    }

    if( length == 0 )
    {
        fprintf( stderr, "Length is 0\n" );
        return 1;
    }

    buffer = (unsigned char *)malloc( length );
    if( buffer == NULL )
    {
        fprintf( stderr, "Out of memory\n" );
        return 1;
    }

    for( i = 0; i < length; i++ )
    {
        if( load_byte( encoding_type, &buffer[ i ], &p_input, &j, &k ) )
        {
            fprintf( stderr, "load_byte failed\n" );
            free( (void *)buffer );
            return 1;
        }
    }

    if( buffer[ length - 1 ] != 0 && buffer[ length - 2 ] != 0 )
    {
        printf( "Decoded data:\n" );
        for( i = 0; i < length; i++ )
        {
            printf( "0x%02X, ", buffer[ i ] );
            if( ((i + 1) % 12) == 0 )
                printf( "\n" );
        }
        printf( "\n" );
    }
    else
    {
        iconv_t conv;

        char *buf8;
        char *p_buf8;
        char *p_buffer;
        size_t buffer_size = length;
        size_t buf8_size = length;

        buf8 = (char *)malloc( buf8_size + 1 );
        if( buf8 == NULL )
        {
            fprintf( stderr, "Out of memory\n" );
            free( (void *)buffer );
            return 1;
        }

        conv = iconv_open( "UTF-8", "UTF-16LE" );
        if( conv == (iconv_t)-1 )
        {
            fprintf( stderr, "iconv_open failed\n" );
            free( (void *)buffer );
            free( (void *)buf8 );
            return 1;
        }

        p_buf8 = &buf8[ 0 ];
        p_buffer = (char *)&buffer[ 0 ];

        if( iconv( conv, &p_buffer, &buffer_size,
                         &p_buf8, &buf8_size ) == -1 )
        {
            fprintf( stderr, "iconv failed\n" );
            ret = 1;
        }
        else
        {
            buf8[ length - buf8_size ] = 0;
            printf( "Decoded string: [%s]\n", buf8 );
        }

        iconv_close( conv );

        free( (void *)buf8 );
    }

    free( (void *)buffer );

    return ret;
}
[http://nanocrew.net/software/nscdec.c](http://nanocrew.net/software/nscdec.c)
[http://nanocrew.net/?p=128](http://nanocrew.net/?p=128)

---

### Post by newbie2 on 2005-09-02
[http://sidequest.org/weblog/archives/2005/08/multicast_from.html](http://sidequest.org/weblog/archives/2005/08/multicast_from.html)

---

