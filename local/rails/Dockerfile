# Using ruby image
FROM ruby:2.6.5

# Set the application directory
WORKDIR /app

# Copy files to container from host .
COPY Gemfile ./
COPY Gemfile.lock ./
COPY entrypoint.sh /usr/bin/

# Install dependencies.(RUN = exec when docker image is created from dockerfile.)
RUN apt-get update -qq && apt-get install -y nodejs postgresql-client \
    && bundle install \
    && sudo chmod 700 /usr/bin/entrypoint.sh

COPY . ./

ENTRYPOINT ["entrypoint.sh"]

# Make port 3000 available for links and/or publish
EXPOSE 3000

# Start service. (CMD = exec when docker container is created from docker image.)
CMD ["rails", "server", "-b", "0.0.0.0"]