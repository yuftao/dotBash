dotBash
=======

Bash Config

Installation

1. clone the repo
<pre>

git clone git@github.com:yuftao/dotBash.git ~/.bash

</pre>

2. Work on the bash profile, the one on ubuntu is ~/.bashrc
   
   Basically the git prompt feature is based on the code from "git-aware-prompt"   
   
   Read the README.md file in the git-aware-prompt first

   Then open and edit this file :

   Add these lines at the top of the file with proper comment:
<pre>
	#Show git branch name in terminal prompt
    export GITAWAREPROMPT=~/.bash/git-aware-prompt
    source $GITAWAREPROMPT/main.sh

</pre>

3. Be very careful about the existing change to PS1, which will be overritten by or overwrite the new rules

   Combine the exist one with the new rules.

   Example on my ubuntu:
   <pre>
#The logic is changed here since the lines belowed will overwrite the config if it is defined at the top of this file
#The original one is:
#if the $color_prompt is "yes"
#PS1="${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ "
#If $color_prompt is not "yes"
#PS1="${debian_chroot:+($debian_chroot)}\u@\h:\w\$ "

#after the combination is:
if [ "$color_prompt" = yes ]; then
    PS1="${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\[$txtcyn\]\$git_branch\[$txtred\]\$git_dirty\[$txtrst\]\$ "
else
    PS1="${debian_chroot:+($debian_chroot)}\u@\h:\w\[$txtcyn\]\$git_branch\[$txtred\]\$git_dirty\[$txtrst\]\$ "
fi

  </pre>
