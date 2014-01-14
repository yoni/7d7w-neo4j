# 7 Databases in 7 Weeks Neo4J Notes

As I go through the Neo4J chapter of Pragmatic Programmer's 7 Databases in 7 Weeks,
I'm taking some notes to ensure that the book club members can all get set up and
running effectively.

### Notes on OS X setup for 7d7w Neo4J

##### Check Prerequisites

    # Double check that your Java version is 7:
    java -version
    mvn -version

    # Double check that homebrew is installed, up to date, and has no issues:
    which brew
    brew update
    brew doctor

##### Install Neo4J 1.9.4 (not 2.0.x)

7d7w uses an older version of neo4j, which has the Gremlin console. Therefore, we'll
need to install an older version using homebrew.

    # See which versions of neo4j are in the homebrew history. We'll look for 1.9.4, which
    # is the last version to support the Gremlin console.
    cd $( brew --prefix )
    brew versions neo4j

    # Check out the 1.9.4 version of the of neo4j brew recipe and install neo4j
    git checkout 8724154 Library/Formula/neo4j.rb
    brew install neo4j

    # Find the neo4j home directory and set NEO4J_HOME
    brew info neo4j
    export NEO4J_HOME=/usr/local/Cellar/neo4j/1.9.4

### Known Issues

In the Gremlin DSL examples, you'll need to initialize the variable start, as reported in Pull Request #1 and #4:
* https://github.com/sevenweeks/databases/pull/1
* https://github.com/sevenweeks/databases/pull/4

The Freebase data for the chapter is no longer available as a simple TSV download. I.e. this returns a 404 error:

    wget http://download.freebase.com/datadumps/latest/browse/film/performance.tsv

To work around this, first download an archived Freebase backup (unfortunately, from 2010):

    wget https://archive.org/download/freebase-data-dump-2010-07-16/freebase-datadump-tsv.tar.bz2



