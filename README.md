# FitnessCoach-AI-Powered-Personalized-Workout-Plans
FitnessCoach uses ML and generative AI to create customized workout plans based on users' fitness goals, body type, and preferences, optimizing their fitness journey.
import random

class FitnessCoach:
    def __init__(self, user_name, fitness_goal, body_type, preferences):
        self.user_name = user_name
        self.fitness_goal = fitness_goal
        self.body_type = body_type
        self.preferences = preferences
        self.workout_plan = []

    def generate_workout_plan(self):
        # Sample workouts for demonstration. A real application would use ML models to personalize this.
        workouts = {
            "weight_loss": ["Cardio", "HIIT", "Cycling"],
            "muscle_gain": ["Weight Lifting", "Resistance Training", "Bodyweight Exercises"],
            "flexibility": ["Yoga", "Stretching", "Pilates"],
            "endurance": ["Running", "Swimming", "Circuit Training"]
        }

        preferred_workouts = workouts.get(self.fitness_goal, [])
        
        # Filtering workouts based on user preferences
        if self.preferences:
            preferred_workouts = [workout for workout in preferred_workouts if workout in self.preferences]
        
        # Generating a weekly plan
        weekly_plan = []
        for day in range(7):
            if preferred_workouts:
                workout = random.choice(preferred_workouts)
                weekly_plan.append(f"Day {day + 1}: {workout}")
            else:
                weekly_plan.append(f"Day {day + 1}: Rest or light activity")
        
        self.workout_plan = weekly_plan

    def display_workout_plan(self):
        print(f"Workout Plan for {self.user_name}:")
        for day_plan in self.workout_plan:
            print(day_plan)

# Example usage
user_name = "Alex"
fitness_goal = "muscle_gain"
body_type = "ectomorph"
preferences = ["Weight Lifting", "Resistance Training"]

fitness_coach = FitnessCoach(user_name, fitness_goal, body_type, preferences)
fitness_coach.generate_workout_plan()
fitness_coach.display_workout_plan()
