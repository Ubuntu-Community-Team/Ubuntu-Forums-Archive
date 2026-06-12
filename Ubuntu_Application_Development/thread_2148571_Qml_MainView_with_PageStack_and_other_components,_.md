---
title: "Qml MainView with PageStack and other components, not working as it should"
date: 2013-05-25
forum: Ubuntu Application Development
---

### Post by KoRnKloWn on 2013-05-25
I'm working on an app using Qml, I have a MainView, it has a Column on the left hand side, and a PageStack right next to it, now, the PageStack isn't working as expected, there's no header or toolbar being added (I have titles for my pages, so a header should be displayed, right???), and the PageStack is overlapping the Column even though I have `anchors.left: myColumn.right` in the PageStack. I also have the model and delegate for a GridView inside the MainView (I wouldn't think those would effect it at all, but I'm quite unfamilliar with Qml). So, is the PageStack supposed to be by itself in a MainView? Is that maybe the reason it's not working? Should I have something like a Rectangle be the root component, and then have the MainView next to the Column?

Any help is greately appreciated, thank you.

---

### Post by KoRnKloWn on 2013-05-26
Well, I found the answer to my own question, the MainView can not be the root, it has to be next to the Column, then the only thing inside of the MainView is the PageStack, the root component can be just about anything, Rectangle, or just Item. So, basically like this:
```

Item {
    Column {
        //Anchor to left hand side and set width
        //Other stuff goes here
    }
    MainView {
        //Anchor to right side of Column
        PageStack {
            Page {
                //Other stuff goes here
            }
            Page {
                //Other stuff goes here
            }
        }
    }
    
}

```

---

