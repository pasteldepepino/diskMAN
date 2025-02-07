#!/bin/bash

echo "Program created by PastelDePepino github: https://github.com/pasteldepepino"

while true; do

  read -p "diskMAN> " command

  if [ "$command" == "list disks" ]; then
    ls /Volumes

  elif [ "$command" == "select disk" ]; then
    read -p "Type disk name: " selected

  elif [ "$command" == "look selected disk" ]; then
    if [ -z "$selected" ]; then
      echo '\a'
      echo "No disk selected."
    else
      ls /Volumes/"$selected"
    fi

  elif [ "$command" == "save disk contents" ]; then
    if [ -z "$selected" ]; then
      echo '\a'
      echo "No disk selected."
    else
      ls /Volumes/"$selected" > ~/Downloads/"$selected".txt
    fi

  elif [ "$command" == "save disks" ]; then
    ls /Volumes > ~/Downloads/disks.txt

  elif [ "$command" == "erase disk" ]; then
    if [ -z "$selected" ]; then
      echo '\a'
      echo "No disk selected"
    else
      read -p "WARNING! PROCEEDING WITH THIS ACTION WILL ERASE ALL OF THE SELECTED DISK CONTENTS. ARE YOU OK WITH THAT (YES/NO)? " confirm
      if [ "$confirm" == "YES" ]; then
        rm -rf /Volumes/"$selected"/*
      else
        echo '\a'
        echo "ACTION CANCELED"
      fi
    fi

  elif [ "$command" == "help" ]; then
    clear
    echo "list disks: list all the disks on the computer"
    echo "select disk: select the disk you will be working with"
    echo "look selected disk: look at the selected disk contents"
    echo "save disk contents: save the contents of the disk on a .txt file in your downloads folder"
    echo "save disks: save all the disks inserted on the computer in a .txt file in the downloads folder"
    echo "erase disk: delete all the disk's contents (it does not format the disk, just deletes the folders and files)"
    echo "copy: copy a file from the selected disk to the downloads folder"
    echo "paste: paste a file from the given path to the selected disk"
    echo "exit: quit this program"

  elif [ "$command" == "exit" ]; then
    echo '\a'
    break
    exit

  elif [ "$command" == "paste" ]; then
    if [ -z "$selected" ]; then
      echo '\a'
      echo "No disk selected"
    else
      read -p "Path to file: " pastefile
      cp "$pastefile" /Volumes/"$selected"
      echo '\a'
    fi

  elif [ "$command" == "copy" ]; then
    if [ -z "$selected" ]; then
      echo '\a'
      echo "No disk selected"
    else
      read -p "File to copy: " copyfile
      cp /Volumes/"$selected"/"$copyfile" ~/Downloads
      echo '\a'
    fi

  else
    echo '\a'
    echo "Unknown command: $command"
    echo 'Type "help" for a list of available commands'
  fi

done
