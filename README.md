# git-conffiles
Store system config files in a git repository. 

Rationale.


Sometimes you change your system configuration but don't immidately
notice that something else then suddenly no longer works.

For example, last week I was trying to get my raspberry pi computers
to accept the default route to the internet (that'd normally be
simple, but the routing on my network isn't as trivial as
usual). Anyway, after a while it worked so I was happy.

Three days later I found out that my android-wifi devices didn't
accept the new config and would simply no longer connect to my
wifi. Oops.

This package would have allowed me to roll back to the version of
three days ago, or at least show me what I changed. In the real
world... This was written after the fact....


The idea is to run the update subcommand from cron every night. Or
maybe even every hour. Then "don't worry" about it as git will store
all the changes efficiently. (on many systems there won't often be a
commit).

The "update" subcommand automatically adds all files marked as config
file in dpkg.

In reality I find that config files that you DO want to change are
often NOT marked as conffiles and that many non-config files ARE. My
repository now tracks changes to 16 readme files!

For this I think this program should come with a list of files "often
not marked as config file". The "init" subcommand (or maybe a new one)
could then also add those files to the tracked list.

If you find such a config file that you changed and should be added to
the list of config files, please do submit it for inclusion here.
