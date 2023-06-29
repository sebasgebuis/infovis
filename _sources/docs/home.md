<h1> Information Visualisation Data Story </h1>

# Introduction
Group: 9
Students: Sebastiaan Gebuis, Anahita Foghahazadeh, Ole Elders, Padma Dhuney

With the rise of the internet over the past decades, the music landscape has undergone significant changes, resulting in a wide array of genres and songs (Aucouturier & Pachet, 2002). Despite this diversity, there are instances where music exhibits remarkable similarities (Aucouturier & Pachet, 2002). One such example is the "millennial whoop," a recurring musical pattern prevalent in songs from the 2010s that imparts a sense of familiarity to listeners (Quartz, 2016). This pattern involves transitioning between the fifth and third notes of the musical scale (Quartz, 2016). Such patterns contribute to the perception of similarity in contemporary music.

This website presents various plots that explore the similarities between songs using the "Audio features and lyrics of Spotify songs" dataset. Through these visualizations, we aim to investigate the extent to which recent music shares common characteristics.

## Research Subject: Diversity of popular music
Different generations often clash heads on lots of topics. Music is no exception to this.
Older generations often claim that music sounds the same nowadays, back in their time music was unique and special.
Newer generations however claim that music is currently more diverse than ever. 

This brings us to our two standpoints:

<em> <strong> Popular songs do not sound the same, diversity in music has increased because of the rise of the internet. </strong> </em>

<em> <strong> Popular music does sound the same, that is why it is all labeled under one label of "pop music" </strong></em>

# Data and Preprocessing

The dataset used for this project is "Audio features and lyrics of Spotify songs" by Muhammad Nakhaee (https://www.kaggle.com/datasets/imuhammad/audio-features-and-lyrics-of-spotify-songs).
This dataset is semi-structured as it is a CSV file.

## Dataset Properties
| Attributes | Records |
| :---: | :---: |
| 25 | 18454 |

## Variable Overview
| Variable | Variable Type | Measurement Scale | Relevant Statistic | 
| :---: | :---: |  :---: |  :---: |
| Track id | Discrete | Nominal | NaN |
| Track name | Discrete | Nominal | NaN |
| Track Artist | Discrete | Nominal | Mode: Queen |
| Lyrics | Discrete | Nominal | NaN |
| Track Popularity | Continuous | Ordinal | Mean: 42.44 | 
| Track album id | Discrete | Nominal | NaN | 
| Track album name | Discrete | Nominal | Mode: Greatest Hits |
| Track album release date | Discrete | Ordinal | Mode: 2013-01-01 |
| Playlist name | Discrete | Nominal | Mode: Indie Poptimism | 
| Playlist id | Discrete | Nominal | Nan | 
| Playlist genre | Discrete | Nominal | Mode: Pop |
| Playlist subgenre | Discrete | Nominal | Mode: Indie Poptimism |
| Danceability | Continuous | Ordinal | Mean: 0.64 | 
| Energy | Continuous | Ordinal | Mean: 0.67 |
| Key | Discrete | Nominal | Mode: 1 (C#/D)|
| Loudness | Continuous | Ordinal | Mean: -6.77 | 
| Mode | Discrete | Nominal | Mode: 1 (Major) |
| Speechiness | Continuous | Ordinal | Mean: 0.11 |
| Acousticness | Continuous | Ordinal | Mean: 0.18 |
| Instrumentalness | Continuous | Ordinal | Mean: 0.05 |
| Liveness | Continuous | Ordinal | Mean: 0.19 |
| Valence | Continuous | Ordinal | Mean: 0.52 |
| Tempo | Continuous | Interval | Mean: 120.81 - Std: 27.59 |
| Duration ms | Continuous | Ratio | Mean: 230319 - Std: 57255.09 |
| Language | Discrete | Nominal | Mode: en (English) |


## Variable description

| Variable | Description |
| :--: | :------: |
| Track id | The unique id given to a song by spotify |
| Track name | The name of a song |
| Track Artist | The artist who made the song |
| Lyrics | The lyrics of the song |
| Track Popularity | The popularity of a song on a scale of 0-100 based on streams |
| Track album id | The unique id given to the album |
| Track album name | The name of the album |
| Track album release date | The release date of the album |
| Playlist name | Name of the playlist in which the song is |
| Playlist id | The unique id of the playlist |
| Playlist genre | The genre of the playlist |
| Playlist subgenre | The subgenre of the playlist |
| Danceability | The danceability of a song, calculated based on the beat strength, tempo stability and overall tempo. A value of 0.0 is least danceable and 1.0 is most danceable |
| Energy | The energy of a song, meassured on a scale of 0.0 - 1.0. Based on the loudness, tempo and amount of noise of a track. A value of 0.0 is least energetic and 1.0 is most energetic |
|  Key | The overall key of a song, mapped to integers using standard Pitch Class notation (0 = C, 1 = C#/D minor, 2 = D) |
| Loudness | The overall loudness of a track in decibels according to LUFS (Loudness Units relative to Full Scale) |
| Mode | Indicates the modality of a track (minor / major). 0 indicates a minor modality, 1 indicates a major modality |
| Speechiness | Detects the presence of spoken words in a track. More exclusive speech-like recordings get closer to a value of 1.0, values between 0.33 and 0.66 indicate both music and speech (rap). Values below 0.33 most likely indicate music and other non-speech-like tracks. |
| Acousticness | Indicates the likeliness that a track is acoustic. A 1.0 indicates high confidence that the track is acoustic, while a 0.0 indicates low confidence that a track is acoustic |
| Instrumentalness | Predicts whether the track contains no vocals. Melodic vocals, such as "Ooh" and "Aah", are considered instrumentals. A value of 1.0 indicates high probability of no spoken words in the track, a 0.0 indicates high probability of spoken words in the track. |
| Liveness | Detects the presence of an audience in the recording. High liveness means a high probability that the track was recorded live, in front of an audience. |
| Valence | Describes the positivity of a track. A value of 0.0 indicates a track of low positivity (angry, sad), a 1.0 indicates high positivity in a track (upbeat, cheerful) |
| Tempo | The tempo of a song in beats per minute (BPM) |
| Duration ms | The duration of a song in miliseconds | 
| Language | The language of a song, abbreviated (en = English) |

## Preprocessing
The dataset was relatively complete, however few changes still needed to take place in order to make full use of the dataset.
<p>
The dataset has a columns named "track_album_release_date". 
In this column the release date of all songs is stated, however some dates were only in years and not in ISO8601.
This made it impossible to use the pandas.to_datetime function in order to make graphs with it. Therefore a function was written which added "-01-01" to the end of all dates which only consisted of a year.
Writing this function allowed for making graphs using the release date as a variable.
</p>

<p>
After changing the dates, the unused columns are dropped. This allows for less resource usage when using the dataset. The columns dropped are: 'language', 'track_id', 'lyrics', 'track_album_id', 'track_album_name', 'playlist_name', 'playlist_id', 'duration_ms'.
</p>

# References

Aucouturier, J. J., & Pachet, F. (2002, October). Music similarity measures: What's the use?. In Ismir (Vol. 7, pp. 339-340).
 

Quartz. (2016, August 28). The “millennial whoop” is taking over pop music [Video]. YouTube. https://www.youtube.com/watch?v=MN23lFKfpck

# Reflection

During the pear review we received valuable feedback from fellow students. Overall, the feedback was very positive and encouraging, which served as a source of motivation and assurance. 


However, several students raised a specific concern regarding the clarity of the scatterplot that was made. The scatterplot provided information about the instrumentalness and acousticness of popular songs. For many students the scatterplot was not clear enough and too confusing. To avoid any misunderstanding among readers, we've decided to remove the scatterplot.


Overall, the feedback was very positive and helpful for the research and has aided in the completion of this research.

# Work Distribution

Sebastiaan Gebuis: Layed the foundation for the project. Made most of the visualisations in the beginning, which were further explored by others. Also responsible for the functioning of the repository / GitHub site. Wrote most of the "home.md" file.

Anahita Foghahazadeh: Found the dataset, further explored visualisations and wrote in depth captions for all visualitions.

Ole Elders: Wrote the introduction in the "home.md" file.

Padma Dhuney: Explored visualisations and wrote the reflection

# Github Repository

The link to the GitHub repository can be found [here](https://github.com/sebasgebuis/infovis) <br>
The link to the GitHub site can be found [here](https://sebasgebuis.github.io/infovis)