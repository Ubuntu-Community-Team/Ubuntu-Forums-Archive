---
title: "libsecret not working with user account space for ubuntu2004"
date: 2021-01-27
forum: Ubuntu Application Development
---

### Post by avinashkhatri1986 on 2021-01-27
I am using libsecret library and facing problem with ubuntu2004 gnome-keyring
I have written below cpp code

[COLOR=#d4d4d4][FONT=Droid Sans Mono][COLOR=#c586c0]#include[/COLOR][COLOR=#569cd6] [/COLOR][COLOR=#ce9178]<libsecret/secret.h>[/COLOR]
[COLOR=#c586c0]#include[/COLOR][COLOR=#569cd6] [/COLOR][COLOR=#ce9178]<iostream>[/COLOR]
[COLOR=#c586c0]#include[/COLOR][COLOR=#569cd6] [/COLOR][COLOR=#ce9178]<time.h>[/COLOR]
[COLOR=#c586c0]#define[/COLOR][COLOR=#569cd6] [/COLOR][COLOR=#569cd6]SCHEMA[/COLOR][COLOR=#569cd6] [/COLOR][COLOR=#dcdcaa]getSchema[/COLOR][COLOR=#569cd6]()[/COLOR]
[COLOR=#c586c0]#define[/COLOR][COLOR=#569cd6] [/COLOR][COLOR=#569cd6]CREDENTIALS_TOKEN_LABEL[/COLOR][COLOR=#569cd6] [/COLOR][COLOR=#ce9178]"ubuntu2004test"[/COLOR]


[COLOR=#569cd6]const[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#4ec9b0]SecretSchema[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#569cd6]*[/COLOR][COLOR=#dcdcaa]getSchema[/COLOR][COLOR=#d4d4d4]([/COLOR][COLOR=#569cd6]void[/COLOR][COLOR=#d4d4d4])[/COLOR]
[COLOR=#d4d4d4]{[/COLOR]
[COLOR=#d4d4d4]    [/COLOR]
[COLOR=#d4d4d4]    [/COLOR][COLOR=#569cd6]static[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#569cd6]const[/COLOR][COLOR=#d4d4d4] SecretSchema [/COLOR][COLOR=#9cdcfe]schema[/COLOR][COLOR=#d4d4d4] = {[/COLOR]
[COLOR=#d4d4d4]        [/COLOR][COLOR=#ce9178]"org.example.credentials"[/COLOR][COLOR=#d4d4d4],[/COLOR]
[COLOR=#d4d4d4]        SECRET_SCHEMA_NONE,[/COLOR]
[COLOR=#d4d4d4]        {[/COLOR]
[COLOR=#d4d4d4]         {[/COLOR][COLOR=#ce9178]"username"[/COLOR][COLOR=#d4d4d4], SECRET_SCHEMA_ATTRIBUTE_STRING},[/COLOR]
[COLOR=#d4d4d4]         {[/COLOR][COLOR=#569cd6]NULL[/COLOR][COLOR=#d4d4d4], (SecretSchemaAttributeType)[/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#d4d4d4]}}};[/COLOR]

[COLOR=#d4d4d4]    [/COLOR][COLOR=#c586c0]return[/COLOR][COLOR=#d4d4d4] &[/COLOR][COLOR=#9cdcfe]schema[/COLOR][COLOR=#d4d4d4];[/COLOR]
[COLOR=#d4d4d4]}[/COLOR]

[COLOR=#569cd6]void[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#dcdcaa]putCredentials[/COLOR][COLOR=#d4d4d4]([/COLOR][COLOR=#4ec9b0]std[/COLOR][COLOR=#d4d4d4]::[/COLOR][COLOR=#4ec9b0]string[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#9cdcfe]username[/COLOR][COLOR=#d4d4d4],[/COLOR][COLOR=#4ec9b0]std[/COLOR][COLOR=#d4d4d4]::[/COLOR][COLOR=#4ec9b0]string[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#9cdcfe]password[/COLOR][COLOR=#d4d4d4])[/COLOR]
[COLOR=#d4d4d4]{[/COLOR]
[COLOR=#d4d4d4]    GError *error = [/COLOR][COLOR=#569cd6]NULL[/COLOR][COLOR=#d4d4d4];[/COLOR]
[COLOR=#d4d4d4]    [/COLOR][COLOR=#dcdcaa]secret_password_store_sync[/COLOR][COLOR=#d4d4d4]([/COLOR][COLOR=#569cd6]SCHEMA[/COLOR][COLOR=#d4d4d4], SECRET_COLLECTION_DEFAULT, [/COLOR][COLOR=#569cd6]CREDENTIALS_TOKEN_LABEL[/COLOR][COLOR=#d4d4d4], [/COLOR][COLOR=#9cdcfe]password[/COLOR][COLOR=#d4d4d4].[/COLOR][COLOR=#dcdcaa]c_str[/COLOR][COLOR=#d4d4d4](), [/COLOR][COLOR=#569cd6]NULL[/COLOR][COLOR=#d4d4d4],[/COLOR]
[COLOR=#d4d4d4]                               &error, [/COLOR][COLOR=#ce9178]"username"[/COLOR][COLOR=#d4d4d4],[/COLOR][COLOR=#9cdcfe]username[/COLOR][COLOR=#d4d4d4].[/COLOR][COLOR=#dcdcaa]c_str[/COLOR][COLOR=#d4d4d4](),[/COLOR][COLOR=#569cd6]NULL[/COLOR][COLOR=#d4d4d4]);[/COLOR]
[COLOR=#d4d4d4]}[/COLOR]
[COLOR=#569cd6]void[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#dcdcaa]deleteAllCredentials[/COLOR][COLOR=#d4d4d4](){[/COLOR]
[COLOR=#d4d4d4]    [/COLOR][COLOR=#4ec9b0]std[/COLOR][COLOR=#d4d4d4]::[/COLOR][COLOR=#9cdcfe]cout[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#dcdcaa]<<[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#d7ba7d]\n[/COLOR][COLOR=#ce9178]Deletting all credential....[/COLOR][COLOR=#d7ba7d]\n[/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#d4d4d4];[/COLOR]
[COLOR=#d4d4d4]    GError *error = [/COLOR][COLOR=#569cd6]NULL[/COLOR][COLOR=#d4d4d4];[/COLOR]
[COLOR=#d4d4d4]    SecretService *sec = [/COLOR][COLOR=#dcdcaa]secret_service_get_sync[/COLOR][COLOR=#d4d4d4](SECRET_SERVICE_LOAD_COLLECTIONS, [/COLOR][COLOR=#569cd6]NULL[/COLOR][COLOR=#d4d4d4], &error);[/COLOR]
[COLOR=#d4d4d4]    _SecretCollection *collection = [/COLOR][COLOR=#569cd6]NULL[/COLOR][COLOR=#d4d4d4];[/COLOR]

[COLOR=#d4d4d4]    collection = [/COLOR][COLOR=#dcdcaa]secret_collection_for_alias_sync[/COLOR][COLOR=#d4d4d4](sec, SECRET_COLLECTION_DEFAULT,[/COLOR]
[COLOR=#d4d4d4]                                     SECRET_COLLECTION_LOAD_ITEMS, [/COLOR][COLOR=#569cd6]NULL[/COLOR][COLOR=#d4d4d4], &error);[/COLOR]
[COLOR=#d4d4d4]    GList *items = [/COLOR][COLOR=#dcdcaa]secret_collection_get_items[/COLOR][COLOR=#d4d4d4](collection);[/COLOR]
[COLOR=#d4d4d4]    [/COLOR][COLOR=#c586c0]for[/COLOR][COLOR=#d4d4d4] ([/COLOR][COLOR=#569cd6]unsigned[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#569cd6]int[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#9cdcfe]i[/COLOR][COLOR=#d4d4d4] = [/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#d4d4d4]; [/COLOR][COLOR=#9cdcfe]i[/COLOR][COLOR=#d4d4d4] < [/COLOR][COLOR=#dcdcaa]g_list_length[/COLOR][COLOR=#d4d4d4](items); [/COLOR][COLOR=#9cdcfe]i[/COLOR][COLOR=#d4d4d4]++)[/COLOR]
[COLOR=#d4d4d4]    {[/COLOR]
[COLOR=#d4d4d4]        SecretItem *item = (SecretItem *)[/COLOR][COLOR=#dcdcaa]g_list_nth_data[/COLOR][COLOR=#d4d4d4](items, i);[/COLOR]
[COLOR=#d4d4d4]        [/COLOR][COLOR=#4ec9b0]std[/COLOR][COLOR=#d4d4d4]::[/COLOR][COLOR=#4ec9b0]string[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#9cdcfe]label[/COLOR][COLOR=#d4d4d4]([/COLOR][COLOR=#dcdcaa]secret_item_get_label[/COLOR][COLOR=#d4d4d4](item));[/COLOR]
[COLOR=#d4d4d4]        [/COLOR][COLOR=#c586c0]if[/COLOR][COLOR=#d4d4d4] ([/COLOR][COLOR=#9cdcfe]label[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#dcdcaa]==[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#569cd6]CREDENTIALS_TOKEN_LABEL[/COLOR][COLOR=#d4d4d4])[/COLOR]
[COLOR=#d4d4d4]        {[/COLOR]
[COLOR=#d4d4d4]            [/COLOR][COLOR=#dcdcaa]secret_item_delete_sync[/COLOR][COLOR=#d4d4d4](item, [/COLOR][COLOR=#569cd6]NULL[/COLOR][COLOR=#d4d4d4], &error);[/COLOR]
[COLOR=#d4d4d4]            [/COLOR][COLOR=#c586c0]if[/COLOR][COLOR=#d4d4d4] (error != [/COLOR][COLOR=#569cd6]NULL[/COLOR][COLOR=#d4d4d4])[/COLOR]
[COLOR=#d4d4d4]            {[/COLOR]
[COLOR=#d4d4d4]                [/COLOR][COLOR=#4ec9b0]std[/COLOR][COLOR=#d4d4d4]::[/COLOR][COLOR=#9cdcfe]cout[/COLOR][COLOR=#dcdcaa]<<[/COLOR][COLOR=#ce9178]"Error: Cannot delete item:"[/COLOR][COLOR=#d4d4d4]<<[/COLOR][COLOR=#9cdcfe]error[/COLOR][COLOR=#d4d4d4]->[/COLOR][COLOR=#9cdcfe]message[/COLOR][COLOR=#d4d4d4];[/COLOR]
[COLOR=#d4d4d4]            }[/COLOR]
[COLOR=#d4d4d4]        }[/COLOR]
[COLOR=#d4d4d4]        [/COLOR][COLOR=#dcdcaa]g_object_unref[/COLOR][COLOR=#d4d4d4](item);[/COLOR]
[COLOR=#d4d4d4]    }[/COLOR]
[COLOR=#d4d4d4]    [/COLOR][COLOR=#dcdcaa]g_list_free[/COLOR][COLOR=#d4d4d4](items);[/COLOR]
[COLOR=#d4d4d4]    [/COLOR][COLOR=#4ec9b0]std[/COLOR][COLOR=#d4d4d4]::[/COLOR][COLOR=#9cdcfe]cout[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#dcdcaa]<<[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#ce9178]"...All credentials deleted..."[/COLOR][COLOR=#d4d4d4];[/COLOR]
[COLOR=#d4d4d4]}[/COLOR]

[COLOR=#569cd6]int[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#dcdcaa]main[/COLOR][COLOR=#d4d4d4]()[/COLOR]
[COLOR=#d4d4d4]{[/COLOR]
[COLOR=#d4d4d4]    [/COLOR][COLOR=#4ec9b0]std[/COLOR][COLOR=#d4d4d4]::[/COLOR][COLOR=#9cdcfe]cout[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#dcdcaa]<<[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#ce9178]"Adding tokens"[/COLOR][COLOR=#d4d4d4];[/COLOR]
[COLOR=#d4d4d4]    [/COLOR][COLOR=#4ec9b0]std[/COLOR][COLOR=#d4d4d4]::[/COLOR][COLOR=#9cdcfe]cout[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#dcdcaa]<<[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#d7ba7d]\n[/COLOR][COLOR=#ce9178]Enter new username or type exit :"[/COLOR][COLOR=#d4d4d4];[/COLOR]
[COLOR=#d4d4d4]    [/COLOR][COLOR=#4ec9b0]std[/COLOR][COLOR=#d4d4d4]::[/COLOR][COLOR=#4ec9b0]string[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#9cdcfe]username[/COLOR][COLOR=#d4d4d4][] = {[/COLOR][COLOR=#ce9178]"user1"[/COLOR][COLOR=#d4d4d4], [/COLOR][COLOR=#ce9178]"user2"[/COLOR][COLOR=#d4d4d4], [/COLOR][COLOR=#ce9178]"user3"[/COLOR][COLOR=#d4d4d4], [/COLOR][COLOR=#ce9178]"user4"[/COLOR][COLOR=#d4d4d4], [/COLOR][COLOR=#ce9178]"user5"[/COLOR][COLOR=#d4d4d4], [/COLOR][COLOR=#ce9178]"user6"[/COLOR][COLOR=#d4d4d4]};[/COLOR]
[COLOR=#d4d4d4]    [/COLOR][COLOR=#4ec9b0]std[/COLOR][COLOR=#d4d4d4]::[/COLOR][COLOR=#4ec9b0]string[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#9cdcfe]password[/COLOR][COLOR=#d4d4d4][] = {[/COLOR][COLOR=#ce9178]"pass1"[/COLOR][COLOR=#d4d4d4], [/COLOR][COLOR=#ce9178]"pass2"[/COLOR][COLOR=#d4d4d4], [/COLOR][COLOR=#ce9178]"pass3"[/COLOR][COLOR=#d4d4d4], [/COLOR][COLOR=#ce9178]"pass4"[/COLOR][COLOR=#d4d4d4], [/COLOR][COLOR=#ce9178]"pass5"[/COLOR][COLOR=#d4d4d4], [/COLOR][COLOR=#ce9178]"pass6"[/COLOR][COLOR=#d4d4d4]};[/COLOR]

[COLOR=#d4d4d4]    [/COLOR][COLOR=#c586c0]for[/COLOR][COLOR=#d4d4d4] ([/COLOR][COLOR=#569cd6]int[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#9cdcfe]i[/COLOR][COLOR=#d4d4d4] = [/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#d4d4d4]; [/COLOR][COLOR=#9cdcfe]i[/COLOR][COLOR=#d4d4d4] < [/COLOR][COLOR=#b5cea8]6[/COLOR][COLOR=#d4d4d4]; [/COLOR][COLOR=#9cdcfe]i[/COLOR][COLOR=#d4d4d4]++)[/COLOR]
[COLOR=#d4d4d4]    {[/COLOR]
[COLOR=#d4d4d4]        [/COLOR][COLOR=#4ec9b0]std[/COLOR][COLOR=#d4d4d4]::[/COLOR][COLOR=#9cdcfe]cout[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#dcdcaa]<<[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#ce9178]"Adding credentials....[/COLOR][COLOR=#d7ba7d]\n[/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#d4d4d4];[/COLOR]
[COLOR=#d4d4d4]        [/COLOR][COLOR=#4ec9b0]std[/COLOR][COLOR=#d4d4d4]::[/COLOR][COLOR=#9cdcfe]cout[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#dcdcaa]<<[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#9cdcfe]username[/COLOR][COLOR=#d4d4d4][[/COLOR][COLOR=#9cdcfe]i[/COLOR][COLOR=#d4d4d4]][/COLOR][COLOR=#dcdcaa]<<[/COLOR][COLOR=#4ec9b0]std[/COLOR][COLOR=#d4d4d4]::[/COLOR][COLOR=#dcdcaa]endl[/COLOR][COLOR=#d4d4d4];[/COLOR]
[COLOR=#d4d4d4]        [/COLOR][COLOR=#4ec9b0]std[/COLOR][COLOR=#d4d4d4]::[/COLOR][COLOR=#9cdcfe]cout[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#dcdcaa]<<[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#9cdcfe]password[/COLOR][COLOR=#d4d4d4][[/COLOR][COLOR=#9cdcfe]i[/COLOR][COLOR=#d4d4d4]][/COLOR][COLOR=#dcdcaa]<<[/COLOR][COLOR=#4ec9b0]std[/COLOR][COLOR=#d4d4d4]::[/COLOR][COLOR=#dcdcaa]endl[/COLOR][COLOR=#d4d4d4];[/COLOR]
[COLOR=#d4d4d4]        [/COLOR][COLOR=#dcdcaa]putCredentials[/COLOR][COLOR=#d4d4d4]([/COLOR][COLOR=#9cdcfe]username[/COLOR][COLOR=#d4d4d4][[/COLOR][COLOR=#9cdcfe]i[/COLOR][COLOR=#d4d4d4]], [/COLOR][COLOR=#9cdcfe]password[/COLOR][COLOR=#d4d4d4][[/COLOR][COLOR=#9cdcfe]i[/COLOR][COLOR=#d4d4d4]]);[/COLOR]
[COLOR=#d4d4d4]        [/COLOR][COLOR=#dcdcaa]sleep[/COLOR][COLOR=#d4d4d4]([/COLOR][COLOR=#b5cea8]3[/COLOR][COLOR=#d4d4d4]);[/COLOR]
[COLOR=#d4d4d4]    }[/COLOR]
[COLOR=#d4d4d4]    [/COLOR][COLOR=#dcdcaa]deleteAllCredentials[/COLOR][COLOR=#d4d4d4]();[/COLOR]
[COLOR=#d4d4d4]    [/COLOR][COLOR=#c586c0]return[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#b5cea8]0[/COLOR][COLOR=#d4d4d4];[/COLOR]
[COLOR=#d4d4d4]}[/COLOR]

[/FONT][/COLOR]

And I compile it using 
g++  ubuntu2004-libsecret.cpp -o test `pkg-config --cflags --libs glib-2.0 libsecret-1`

I have below shell script
[COLOR=#d4d4d4][FONT=Droid Sans Mono][COLOR=#6a9955]#!/bin/bash[/COLOR]
[COLOR=#d4d4d4]location=[/COLOR][COLOR=#ce9178]"/home/avinash/Documents/training/"[/COLOR]
[COLOR=#d4d4d4]EXE_CMD=[/COLOR][COLOR=#9cdcfe]$location[/COLOR][COLOR=#ce9178]"test"[/COLOR]
[COLOR=#dcdcaa]echo[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#9cdcfe]$EXE_CMD[/COLOR]
[COLOR=#c586c0]if[/COLOR][COLOR=#d4d4d4] [ [/COLOR][COLOR=#ce9178]`whoami`[/COLOR][COLOR=#d4d4d4] = [/COLOR][COLOR=#ce9178]"root"[/COLOR][COLOR=#d4d4d4] ][/COLOR]
[COLOR=#c586c0]then[/COLOR]
[COLOR=#d4d4d4]        [/COLOR][COLOR=#dcdcaa]echo[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#ce9178]"adding in user account: "`logname`[/COLOR]
[COLOR=#d4d4d4]        runuser -l  [/COLOR][COLOR=#ce9178]`logname`[/COLOR][COLOR=#d4d4d4] -c [/COLOR][COLOR=#ce9178]"[/COLOR][COLOR=#9cdcfe]$EXE_CMD[/COLOR][COLOR=#ce9178] 2>/dev/null"[/COLOR]
[COLOR=#c586c0]else[/COLOR][COLOR=#d4d4d4]   [/COLOR]
[COLOR=#d4d4d4]        [/COLOR][COLOR=#9cdcfe]$EXE_CMD[/COLOR][COLOR=#d4d4d4] 2>/dev/null[/COLOR]

[COLOR=#c586c0]fi[/COLOR]

[/FONT][/COLOR]


I get below results "sh ./
Ubuntu 1804: users added and removed in user account ,with and without sudo 
Ubuntu 2004: users added and removed in user account only without sudo, sudo run does not add and remove credentials to user account here.

Any help for ubuntu2004 will be appreciated.

---

