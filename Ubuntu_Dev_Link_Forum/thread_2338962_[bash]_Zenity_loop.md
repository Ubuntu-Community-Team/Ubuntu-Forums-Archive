---
title: "[bash] Zenity loop"
date: 2016-10-03
forum: Ubuntu Dev Link Forum
---

### Post by flammeru on 2016-10-03
Hello folks,

I have created a small gui wich allow me to select a menu to access a sub menu .

My issue is when i pressed cancel it does not go back to the main menu however it works for the first one "go to menu" but not for the others .

appreciate some help i am stuck here is the full code :
```
#!/bin/bash


while true; do
  choice="$(zenity --width=200 --height=150 --list --column "" --title="test" \
  "Go to next menu" \
 "test2" \
"test" \
"test3" \
"test4" 


  "Exit ")"


  case "${choice}" in
    "Go to next menu" )
      while true; do
        choice2="$(zenity --width=200 --height=150 --list --column "" --title="test" \
        "Do Something" \
        "Do Something Else " \
        "Back")"


        case "${choice2}" in
          "Do Something" )
            echo "hello"
          ;;
          "Do Something Else " )
            echo "hello"
          ;;
          *)
            break
          ;;
        esac
      done
    ;;
    *)
      break
    ;;
esac
done
case "${choice}" in
    "test2" )
      while true; do
        choice0="$(zenity --width=200 --height=150 --list --column "" --title="test" \
        "Do Something" \
        "Do Something Else " \
        "Back")"


        case "${choice0}" in
          "Do Something" )
            echo "hello"
          ;;
          "Do Something Else " )
            echo "hello"
          ;;


         *)


            break
         
          ;;
        esac
      done
    ;;
    *)
      break
    ;;
  esac


  case "${choice}" in
    "test" )
      while true; do
        choice3="$(zenity --width=200 --height=150 --list --column "" --title="test" \
        "Do Something" \
        "Do Something Else " \
        "Back")"


        case "${choice3}" in
          "Do Something" )
            echo "hello"
          ;;
          "Do Something Else " )
            echo "hello"
          ;;
          *)
            break
          ;;
        esac
      done
    ;;
    *)
      break
    ;;
  esac
don e
 case "${choice}" in
    "test3" )
      while true; do
        choice4="$(zenity --width=200 --height=150 --list --column "" --title="test" \
        "Do Something" \
        "Do Something Else " \
        "Back")"


        case "${choice4}" in
          "Do Something" )
            echo "hello"
          ;;
          "Do Something Else " )
            echo "hello"
          ;;
          *)
            break
          ;;
        esac
      done
    ;;
    *)
      break
    ;;
esac


 case "${choice}" in
    "test4" )
      while true; do
        choice5="$(zenity --width=200 --height=150 --list --column "" --title="test" \
        "Do Something" \
        "Do Something Else " \
        "Back")"


        case "${choice5}" in
          "Do Something" )
            echo "hello"
          ;;
          "Do Something Else " )
            echo "hello"
          ;;
          *)
            break
          ;;
        esac
      done
    ;;
    *)
      break
    ;;
esac
done


 







```

---

