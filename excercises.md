# HTTP requests

## Story

One of the local school's system administrator has won the lottery then quit and left the country. Sadly no-one knows how to operate the school's student database because it has no GUI and it can only be used with API calls. They contact you and ask you for your help with accessing and manipulating student data.

## What are you going to learn?

A list of things, concepts, tools, etc. that the students will learn by doing this exercises.
- Interacting with APIs
- Making HTTP requests
- HTTP response codes

## Tasks

**Task 1**: Send HTTP requests via an API client
- Requirement 1a: install [Postman](https://www.postman.com/)
- Requirement 1b: make a request to any url and check the results

**Task 2**: Set-up a webserver from a docker image
- Requirement 2a: create a `docker-compose.yml` file that contains the following:

      version: '3.7'

      services:
        web:
          image: sandormatyas/student_api_web:latest
          command: bash -c "bash /usr/src/app/entrypoint.sh && python manage.py run -h 0.0.0.0"
          ports:
            - 5000:5000
          depends_on:
            - db
        db:
          image: postgres:12-alpine
          volumes:
            - postgres_data:/var/lib/postgresql/data/
          environment:
            - POSTGRES_USER=postgres
            - POSTGRES_PASSWORD=postgres
            - POSTGRES_DB=students

      volumes:
        postgres_data:



- Requirement 2c: run `docker-compose up` to start the server

- Requirement 2d: make a request with Postman to the server (will run at http://localhost:5000)
- Requirement 2e: familiarize yourself with the API (/endpoints)

**Task 3**: Playing around with the API
- Requirement 3a: get the information of all students. Try setting the Content-Type header to `application/json` / `text/plain`.

- Requirement 3b: register 2 new students with the correct endpoint and request method.
- Requirement 3c: change some or all of the data of a student with the correct endpoint and request method.
- Requirement 3d: delete a student with the correct endpoint and request method.

**Task 4**: make requests to the following endpoints with the focus on response codes

Before starting this task make sure to turn off `'Automatically follow redirects'` in the settings of Postman.

- Requirement 4a: GET /students

- Requirement 4b: GET /information
- Requirement 4c: GET /teachers
- Requirement 4d: POST /students
- Requirement 4e: POST /students with an invalid key (e.g. with "name" key instead of "first_name" or "last_name")
- Requirement 4f: GET /students/Jimmy


## Background materials

A list of useful videos, articles, etc. which if read can help solve the assignment.
- [What are APIs?](https://www.youtube.com/watch?v=OVvTv9Hy91Q)
- [Basics of HTTP](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview)
- [HTTP response codes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)
