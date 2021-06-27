current-fm
=============

a dead simple ruby utililty to connect to last-fm, get your most recent playing song, and write it to a file

Why?
----

basically so i can use the now-playing plugin for tmux-powerline, that's all to it honestly

Installation
------------

Clone the application
```
$ git clone https://github.com/oz-codes/current-fm.git
```

Usage
-----

To use current-fm, all you have to do is run `cfm`

The first time you run this, if you did not already do so, it will create a file in your home directory called ~/.cfm.json which with some placeholder fields in it for you to fill in. The two fields in question are:
```
  {
    'api_key':    <YOUR_LAST_FM_API_KEY>,
    'api_secret': <YOUR_LAST_FM_API_SECRET>,
    'output':     '/path/to/desired/output.file'
  }
```
note: if you don't include the api_key and api_secret, it will pretty much run home crying and just not work. kinda necessary. aside from that, if you don't define output, it will default to ~/cfm.np (which will be the default path in the generated file)

From here, all you have to do is set up a cron job (or whatever scheduling system you choose to use) to get this to run regularly. If you run cfm --cron, it will spit out a suggested cron line for you to use that updates every 5 minutes.

That's basically it.

Included rake tasks
```
$ bundle exec rake 
rake deez:nuts
rake got:heem
```

Some basic tests under the `test` folder
```
$ bundle exec rake test
Run options: --seed 29770

# Running:

...

Finished in 0.004737s, 633.3162 runs/s, 633.3162 assertions/s.

3 runs, 3 assertions, 0 failures, 0 errors, 0 skips
```

Example migration under `db/migrate`
```
$ bundle exec rake db:migrate
== 1 Schema: migrating ========================================================
-- create_table(:users, {:force=>true})
   -> 0.0026s
== 1 Schema: migrated (0.0027s) ===============================================
```

Running the included `app.rb` under `lib/current-fm` via the executable in `bin`
```
$ bundle exec bin/cfm 
#<OpenStruct something="something">
Running application
User Saved
```

License
-------

WTFPL.
