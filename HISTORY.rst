.. :changelog:

History
-------

v0.26.3 (2025-01-06)
....................

* Fix negative expires_ms and avoid worker freezing while using cron by @Matvey-Kuk in #479
* Fix race condition on task retry by @RB387 in #487


v0.26.1 (2023-08-29)
....................

* Uses ``testcontainers`` to provide a redis instance for the unit tests by @chrisguidry in #470
* Bump ``redis`` version from <5 to <6 by @Wh1isper in #460
* Bump ``idna`` from 3.6 to 3.7 in /requirements by @dependabot in #444
* Bump ``jinja2`` from 3.1.3 to 3.1.4 in /requirements by @dependabot in #452
* Bump ``requests`` from 2.31.0 to 2.32.0 in /requirements by @dependabot in #461
* Bump ``urllib3`` from 2.2.1 to 2.2.2 in /requirements by @dependabot in #464
* Bump ``certifi`` from 2024.2.2 to 2024.7.4 in /requirements by @dependabot in #468

v0.26.0 (2023-05-01)
....................

No changes since v0.26.0b1.

v0.26.0b1 (2023-04-01)
......................

* Prevent worker getting stuck in terminating state by @JonasKs in #370
* Fix redis pipeline created and not used by @iamlikeme in #374
* Bump certifi from 2022.6.15 to 2022.12.7 in ``/requirements`` by @dependabot in #373
* Use instance's default queue for ``queued_jobs`` default by @phy1729 in #368
* Docs: Add details about reusing a unique job id by @ross-nordstrom in #391
* Delete ``setup.py`` in #398
* Adding a job counter to address ``Semaphore`` issues by @rm-21 in #408
* docs: add documentation on how to retrieve running jobs by @JonasKs in #377
* feat: add ``job_id`` to ``JobDef``, closing #376 by @JonasKs in #378
* chore: update dependencies, fixing tests by @JonasKs in #382
* refactor: refactor all asserts into raise ``<exception>``, close #371 by @JonasKs in #379
* Fix: timezone info occasionally removed from cron job execution time by @iamlikeme in #383
* 3.12 support, drop 3.7, uprev dependencies by @samuelcolvin in #439
* Extend ``RedisSettings`` to include redis Retry Helper settings by @mernmic in #387
* Allow to connect to Redis using a Unix socket URL… by @drygdryg in #392
* Allow infinite retry by @vvmruder in #396
* Allow ``max_connections`` to be set in RedisSettings by @danbox in #406
* Improve ``RedisSettings`` explanation in ``main_demo.py`` by @RamonGiovane in #422
* uprev to v0.26.0b1 by @samuelcolvin in #440

v0.25 (2022-12-02)
..................

* Allow to opt-out from logging results by @iamlikeme in #352
* Add timezone support for cron jobs by @iamlikeme in #354
* connections: fix pipeline usage for exists command by @utkarshgupta137 in #366
* Fix race condition causing incorrect status not found by @iamlikeme in #362
* Adds ``after_job_end`` hook by @AngellusMortis in #355
* Raise ``ResultNotFound`` when ``Job.result()`` finds no job and no result by @iamlikeme in #364
* use ``3.11`` for testing #367
* Signal handler to wait for task completion before shutting down by @JonasKs in #345

v0.24 (2022-09-05)
..................

* Allow customisation of timezone in logs, #281
* Add the ``username`` option to ``RedisSettings``, #299
* Change primary branch name to ``main``, 40c8803
* Add ``--custom-log-dict`` CLI option, #294
* Fix error in case of pytz not being installed, #318
* Support and test python 3.11, #327
* Improve docs for parameter ``_expires`` in ``enqueue_job``, #313
* Fix redis ssl support, #323
* Fix recursion while waiting for redis connection, #311
* switch from watchgod to watchfiles, #332
* Simplify dependencies, drop pydantic as a dependency., #334
* Allow use of ``unix_socket_path`` in ``RedisSettings``, #336
* Allow user to configure a default job expiry-extra length, #303
* Remove transaction around ``info`` command to support Redis 6.2.3, #338
* Switch from ``setup.py`` to ``pyproject.toml``, #341
* Support ``abort`` for deferred jobs, #307

v0.23 (2022-08-23)
..................

No changes from **v0.23a1**.

v0.23a1 (2022-03-09)
....................
* Fix jobs timeout by @kiriusm2 in #248
* Update ``index.rst`` by @Kludex in #266
* Improve some docs wording by @johtso in #285
* fix error when cron jobs were terminanted by @tobymao in #273
* add ``on_job_start`` and ``on_job_end`` hooks by @tobymao in #274
* Update argument docstring definition by @sondrelg in #278
* fix tests and uprev test dependencies, #288
* Add link to WorkerSettings in documentation by @JonasKs in #279
* Allow setting ``job_id`` on cron jobs by @JonasKs in #293
* Fix docs typo by @johtso in #296
* support aioredis v2 by @Yolley in #259
* support python 3.10, #298

v0.22 (2021-09-02)
..................
* fix package importing in example, #261, thanks @cdpath
* restrict ``aioredis`` to ``<2.0.0`` (soon we'll support ``aioredis>=2.0.0``), #258, thanks @PaxPrz
* auto setting version on release, 759fe03

v0.21 (2021-07-06)
..................
* CI improvements #243
* fix ``log_redis_info`` #255

v0.20 (2021-04-26)
..................

* Added ``queue_name`` attribute to ``JobResult``, #198
* set ``job_deserializer``, ``job_serializer`` and ``default_queue_name`` on worker pools to better supported
  nested jobs, #203, #215 and #218
* All job results to be kept indefinitely, #205
* refactor ``cron`` jobs to prevent duplicate jobs, #200
* correctly handle ``CancelledError`` in python 3.8+, #213
* allow jobs to be aborted, #212
* depreciate ``pole_delay`` and use correct spelling ``poll_delay``, #242
* docs improvements, #207 and #232

v0.19.1 (2020-10-26)
....................

* fix timestamp issue in _defer_until without timezone offset, #182
* add option to disable signal handler registration from running inside other frameworks, #183
* add ``default_queue_name`` to ``create_redis_pool`` and ``ArqRedis``, #191
* ``Worker`` can retrieve the ``queue_name`` from the connection pool, if present
* fix potential race condition when starting jobs, #194
* support python 3.9 and pydantic 1.7, #214

v0.19.0 (2020-04-24)
....................
* Python 3.8 support, #178
* fix concurrency with multiple workers, #180
* full mypy coverage, #181

v0.18.4 (2019-12-19)
....................
* Add ``py.typed`` file to tell mypy the package has type hints, #163
* Added ``ssl`` option to ``RedisSettings``, #165

v0.18.3 (2019-11-13)
....................
* Include ``queue_name`` when for job object in response to ``enqueue_job``, #160

v0.18.2 (2019-11-01)
....................
* Fix cron scheduling on a specific queue, by @dmvass and @Tinche

v0.18.1 (2019-10-28)
....................
* add support for Redis Sentinel fix #132
* fix ``Worker.abort_job`` invalid expire time error, by @dmvass

v0.18 (2019-08-30)
..................
* fix usage of ``max_burst_jobs``, improve coverage fix #152
* stop lots of ``WatchVariableError`` errors in log, #153

v0.17.1 (2019-08-21)
....................
* deal better with failed job deserialization, #149 by @samuelcolvin
* fix ``run_check(xmax_burst_jobs=...)`` when a jobs fails, #150 by @samuelcolvin

v0.17 (2019-08-11)
..................
* add ``worker.queue_read_limit``, fix #141, by @rubik
* custom serializers, eg. to use msgpack rather than pickle, #143 by @rubik
* add ``ArqRedis.queued_jobs`` utility method for getting queued jobs while testing, fix #145 by @samuelcolvin

v0.16.1 (2019-08-02)
....................
* prevent duplicate ``job_id`` when job result exists, fix #137
* add "don't retry mode" via ``worker.retry_jobs = False``, fix #139
* add ``worker.max_burst_jobs``

v0.16 (2019-07-30)
..................
* improved error when a job is aborted (eg. function not found)

v0.16.0b3 (2019-05-14)
......................
* fix semaphore on worker with many expired jobs

v0.16.0b2 (2019-05-14)
......................
* add support for different queues, #127 thanks @tsutsarin

v0.16.0b1 (2019-04-23)
......................
* use dicts for pickling not tuples, better handling of pickling errors, #123

v0.16.0a5 (2019-04-22)
......................
* use ``pipeline`` in ``enqueue_job``
* catch any error when pickling job result
* add support for python 3.6

v0.16.0a4 (2019-03-15)
......................
* add ``Worker.run_check``, fix #115

v0.16.0a3 (2019-03-12)
......................
* fix ``Worker`` with custom redis settings

v0.16.0a2 (2019-03-06)
......................
* add ``job_try`` argument to ``enqueue_job``, #113
* adding ``--watch`` mode to the worker (requires ``watchgod``), #114
* allow ``ctx`` when creating Worker
* add ``all_job_results`` to ``ArqRedis``
* fix python path when starting worker

v0.16.0a1 (2019-03-05)
......................
* **Breaking Change:** **COMPLETE REWRITE!!!** see docs for details, #110

v0.15.0 (2018-11-15)
....................
* update dependencies
* reconfigure ``Job``, return a job instance when enqueuing tasks #93
* tweaks to docs #106

v0.14.0 (2018-05-28)
....................
* package updates, particularly compatibility for ``msgpack 0.5.6``

v0.13.0 (2017-11-27)
....................
* **Breaking Change:** integration with aioredis >= 1.0, basic usage hasn't changed but
  look at aioredis's migration docs for changes in redis API #76

v0.12.0 (2017-11-16)
....................
* better signal handling, support ``uvloop`` #73
* drain pending tasks and drain task cancellation #74
* add aiohttp and docker demo ``/demo`` #75

v0.11.0 (2017-08-25)
....................
* extract ``create_pool_lenient`` from ``RedixMixin``
* improve redis connection traceback

v0.10.4 (2017-08-22)
....................
* ``RedisSettings`` repr method
* add ``create_connection_timeout`` to connection pool

v0.10.3 (2017-08-19)
....................
* fix bug with ``RedisMixin.get_redis_pool`` creating multiple queues
* tweak drain logs

v0.10.2 (2017-08-17)
....................
* only save job on task in drain if re-enqueuing
* add semaphore timeout to drains
* add key count to ``log_redis_info``

v0.10.1 (2017-08-16)
....................
* correct format of ``log_redis_info``

v0.10.0 (2017-08-16)
....................
* log redis version when starting worker, fix #64
* log "connection success" when connecting to redis after connection failures, fix #67
* add job ids, for now they're just used in logging, fix #53

v0.9.0 (2017-06-23)
...................
* allow set encoding in msgpack for jobs #49
* cron tasks allowing scheduling of functions in the future #50
* **Breaking change:** switch ``to_unix_ms`` to just return the timestamp int, add ``to_unix_ms_tz`` to
  return tz offset too

v0.8.1 (2017-06-05)
...................
* uprev setup requires
* correct setup arguments

v0.8.0 (2017-06-05)
...................
* add ``async-timeout`` dependency
* use async-timeout around ``shadow_factory``
* change logger name for control process log messages
* use ``Semaphore`` rather than ``asyncio.wait(...return_when=asyncio.FIRST_COMPLETED)`` for improved performance
* improve log display
* add timeout and retry logic to ``RedisMixin.create_redis_pool``

v0.7.0 (2017-06-01)
...................
* implementing reusable ``Drain`` which takes tasks from a redis list and allows them to be execute asynchronously.
* Drain uses python 3.6 ``async yield``, therefore **python 3.5 is no longer supported**.
* prevent repeated identical health check log messages

v0.6.1 (2017-05-06)
...................
* mypy at last passing, #30
* adding trove classifiers, #29

v0.6.0 (2017-04-14)
...................
* add ``StopJob`` exception for cleaning ending jobs, #21
* add ``flushdb`` to ``MockRedis``, #23
* allow configurable length job logging via ``log_curtail`` on ``Worker``, #28

v0.5.2 (2017-02-25)
...................
* add ``shadow_kwargs`` method to ``BaseWorker`` to make customising actors easier.

v0.5.1 (2017-02-25)
...................
* reimplement worker reuse as it turned out to be useful in tests.

v0.5.0 (2017-02-20)
...................
* use ``gather`` rather than ``wait`` for startup and shutdown so exceptions propagate.
* add ``--check`` option to confirm arq worker is running.

v0.4.1 (2017-02-11)
...................
* fix issue with ``Concurrent`` class binding with multiple actor instances.

v0.4.0 (2017-02-10)
...................
* improving naming of log handlers and formatters
* upgrade numerous packages, nothing significant
* add ``startup`` and ``shutdown`` methods to actors
* switch ``@concurrent`` to return a ``Concurrent`` instance so the direct method is accessible via ``<func>.direct``

v0.3.2 (2017-01-24)
...................
* improved solution for preventing new jobs starting when the worker is about to stop
* switch ``SIGRTMIN`` > ``SIGUSR1`` to work with mac

v0.3.1 (2017-01-20)
...................
* fix main process signal handling so the worker shuts down when just the main process receives a signal
* re-enqueue un-started jobs popped from the queue if the worker is about to exit

v0.3.0 (2017-01-19)
...................
* rename settings class to ``RedisSettings`` and simplify significantly

v0.2.0 (2016-12-09)
...................
* add ``concurrency_enabled`` argument to aid in testing
* fix conflict with unitest.mock

v0.1.0 (2016-12-06)
...................
* prevent logs disabling other logs

v0.0.6 (2016-08-14)
...................
* first proper release
