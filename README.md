<h1>ExpNo 1 :Developing AI Agent with PEAS Description</h1>
<h3>Name: SHASHWATH G S </h3>
<h3>Register Number/Staff Id:212224030026 </h3>


<h3>AIM:</h3>
<br>
<p>To find the PEAS description for the given AI problem and develop an AI agent.</p>
<br>
<h3>Theory</h3>
<h3>Medicine prescribing agent:</h3>
<p>Such this agent prescribes medicine for fever (greater than 98.5 degrees) which we consider here as unhealthy, by the user temperature input, and another environment is rooms in the hospital (two rooms). This agent has to consider two factors one is room location and an unhealthy patient in a random room, the agent has to move from one room to another to check and treat the unhealthy person. The performance of the agent is calculated by incrementing performance and each time after treating in one room again it has to check another room so that the movement causes the agent to reduce its performance. Hence, agents prescribe medicine to unhealthy.</p>
<hr>
<h3>PEAS DESCRIPTION:</h3>
<table>
  <tr>
    <td><strong>Agent Type</strong></td>
    <td><strong>Performance</strong></td>
     <td><strong>Environment</strong></td>
    <td><strong>Actuators</strong></td>
    <td><strong>Sensors</strong></td>
  </tr>
    <tr>
    <td><strong>Medicine prescribing agent</strong></td>
    <td><strong>Treating unhealthy, agent movement</strong></td>
     <td><strong>Rooms, Patient</strong></td>
    <td><strong>Medicine, Treatment</strong></td>
    <td><strong>Location, Temperature of patient</strong></td>
  </tr>
</table>
<hr>
<H3>DESIGN STEPS</H3>
<h3>STEP 1:Identifying the input:</h3>
<p>Temperature from patients, Location.</p>
<h3>STEP 2:Identifying the output:</h3>
<p>Prescribe medicine if the patient in a random has a fever.</p>
<h3>STEP 3:Developing the PEAS description:</h3>
<p>PEAS description is developed by the performance, environment, actuators, and sensors in an agent.</p>
<h3>STEP 4:Implementing the AI agent:</h3>
<p>Treat unhealthy patients in each room. And check for the unhealthy patients in random room</p>
<h3>STEP 5:</h3>
<p>Measure the performance parameters: For each treatment performance incremented, for each movement performance decremented</p>

INPUT:

class MedicinePrescribingAgent:
    def __init__(self):
        self.performance = 0  # counts correct prescriptions
        self.environment = {
            "Room1": {"patient": True, "temperature": 39},  # fever patient
            "Room2": {"patient": False, "temperature": 36}  # healthy room
        }
        self.current_room = "Room1"

    # Sensors
    def sense(self):
        room_state = self.environment[self.current_room]
        return room_state["patient"], room_state["temperature"]

    # Actuators (move, treat)
    def move(self, room):
        print(f"\nMoving to {room}...")
        self.current_room = room

    def prescribe(self, patient, temperature):
        if patient and temperature > 38:
            print("Patient detected with fever! Prescribing medicine...")
            self.performance += 1
        elif not patient:
            print("No patient here. No medicine prescribed.")
        else:
            print("Patient healthy. No medicine needed.")

    # Main agent logic
    def run(self):
        for room in self.environment:
            self.move(room)
            patient, temp = self.sense()
            print(f"Sensed → Patient: {patient}, Temp: {temp}°C")
            self.prescribe(patient, temp)

        print(f"\nFinal Performance Score: {self.performance}")


# Run the simulation
agent = MedicinePrescribingAgent()
agent.run()

![WhatsApp Image 2025-10-03 at 16 15 07_fa94a012](https://github.com/user-attachments/assets/898bde00-2bee-4874-b70f-ccd2a41c4076)
